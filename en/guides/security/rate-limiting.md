# Rate Limiting

Rate limiting is a critical security feature in AACSearch that prevents abuse by limiting the number of API requests a client can make within a specific time frame. This guide explains how rate limiting works, how to handle rate limit errors, and best practices to ensure your application operates within these limits.

## Why Rate Limiting Matters

Rate limiting protects both AACSearch and your application by:

- **Preventing Abuse**: It stops malicious or misconfigured clients from overwhelming the system with excessive requests, which could degrade performance for all users.
- **Ensuring Fair Usage**: It ensures that no single client monopolizes resources, allowing fair access for all users.
- **Maintaining Stability**: It helps maintain the stability and reliability of the AACSearch platform by controlling request volume.

Each AACSearch plan includes a specific rate limit, which is detailed in your account dashboard under "Plan & Billing." Higher-tier plans typically offer higher limits to accommodate increased usage.

## How Rate Limiting Works

AACSearch implements rate limiting based on API keys. Each API key is associated with a specific rate limit, measured as the number of requests allowed per minute or per hour, depending on your plan.

- **Limit Scope**: Rate limits apply to all API endpoints collectively (e.g., search, indexing, analytics) unless otherwise specified.
- **Time Window**: Limits are calculated over a rolling time window. For example, if your limit is 100 requests per minute, it resets gradually as time passes within that minute.
- **Identification**: Limits are tied to your API key, so requests from different keys are counted separately.

When you exceed your rate limit, AACSearch responds with a `429 Too Many Requests` error, indicating that you must wait before making additional requests.

## Checking Your Rate Limits

You can check your current rate limit and usage in the AACSearch Dashboard:

1. Log in to the [AACSearch Dashboard](https://dashboard.aacsearch.com).
2. Navigate to "Settings" > "API Keys."
3. Select the API key you are using to view its associated rate limit and current usage statistics.
4. Alternatively, go to "Plan & Billing" to see the overall limits for your account plan.

Additionally, API responses include headers that provide information about your rate limit status:

- `X-Rate-Limit-Limit`: The maximum number of requests allowed in the current time window.
- `X-Rate-Limit-Remaining`: The number of requests remaining in the current time window.
- `X-Rate-Limit-Reset`: The time (in Unix epoch seconds) when the rate limit window resets.

### Example Response Headers

```http
HTTP/1.1 200 OK
X-Rate-Limit-Limit: 100
X-Rate-Limit-Remaining: 47
X-Rate-Limit-Reset: 1673365200
```

These headers allow your application to monitor usage programmatically and adjust behavior to avoid hitting the limit.

## Handling Rate Limit Errors

When you exceed your rate limit, AACSearch returns a `429 Too Many Requests` error with a JSON response body and specific headers to help you manage the situation.

### Example Error Response

```json
{
  "error": {
    "code": 429,
    "message": "Rate limit exceeded. Please wait before making more requests.",
    "details": {
      "limit": 100,
      "remaining": 0,
      "reset": 1673365200
    }
  }
}
```

### Response Headers for Rate Limit Errors

- `Retry-After`: The number of seconds to wait before making another request. This header is included in `429` responses to indicate how long you must wait.

### Example Error Headers

```http
HTTP/1.1 429 Too Many Requests
X-Rate-Limit-Limit: 100
X-Rate-Limit-Remaining: 0
X-Rate-Limit-Reset: 1673365200
Retry-After: 30
```

### Strategies for Handling Rate Limits

To handle rate limit errors gracefully in your application:

1. **Implement Retry Logic**: When you receive a `429` error, check the `Retry-After` header and wait the specified number of seconds before retrying the request. Use exponential backoff for subsequent retries if needed.
   - **Example in JavaScript (using Fetch API)**:
     ```javascript
     async function makeRequestWithRetry(url, options) {
       let retries = 0;
       const maxRetries = 3;
       while (retries < maxRetries) {
         try {
           const response = await fetch(url, options);
           if (response.status === 429) {
             const retryAfter = response.headers.get("Retry-After");
             const waitTime = retryAfter
               ? parseInt(retryAfter) * 1000
               : Math.pow(2, retries) * 1000;
             console.log(
               `Rate limit exceeded. Waiting for ${waitTime / 1000} seconds...`
             );
             await new Promise((resolve) => setTimeout(resolve, waitTime));
             retries++;
             continue;
           }
           if (!response.ok)
             throw new Error(`HTTP error! Status: ${response.status}`);
           return await response.json();
         } catch (error) {
           console.error("Request failed:", error);
           retries++;
           if (retries === maxRetries) throw error;
           await new Promise((resolve) =>
             setTimeout(resolve, Math.pow(2, retries) * 1000)
           );
         }
       }
       throw new Error("Max retries reached");
     }
     ```
2. **Monitor Usage**: Track the `X-Rate-Limit-Remaining` header to proactively slow down or pause requests as you approach the limit.
3. **Queue Requests**: Implement a request queue to manage high-volume operations, ensuring requests are sent at a controlled pace.
4. **Batch Operations**: For operations like indexing, use batch requests to update multiple objects in a single API call, reducing the total number of requests. See [Objects API](../../api/objects.md) for batch operation details.
5. **Handle Errors Gracefully**: Display user-friendly messages if rate limits cause delays, especially in user-facing applications like search interfaces.

## Best Practices to Avoid Rate Limits

To minimize the chance of hitting rate limits and ensure smooth operation of your application:

- **Optimize API Usage**:
  - Cache frequent search results on your end to reduce redundant API calls. See [Caching Strategies](../performance/caching.md) for implementation tips.
  - Use filters and parameters to narrow down search results instead of making multiple broad queries. See [Search API](../../api/search.md) for parameter details.
  - Batch data uploads or updates whenever possible to minimize request count. See [Objects API](../../api/objects.md) for batch operations.
- **Distribute Load**:
  - Spread API requests evenly over time rather than sending bursts of requests. Implement throttling in your application to pace requests.
  - If you have multiple API keys (e.g., for different environments or applications), rotate usage to distribute load across keys.
- **Upgrade Your Plan**:
  - If your application consistently hits rate limits due to high usage, consider upgrading to a higher-tier plan with increased limits. Check available plans in the [AACSearch Dashboard](https://dashboard.aacsearch.com) under "Plan & Billing."
- **Monitor Usage Trends**:
  - Use the [Analytics API](../../api/analytics.md) to track API usage patterns and identify spikes or inefficiencies in request volume. Adjust your application logic based on these insights.

## Rate Limiting for Different Plans

Rate limits vary depending on your subscription plan. Below is an overview of typical limits for different tiers (exact limits may vary; check your dashboard for current values):

- **Free Plan**: Limited to 100 requests per minute, suitable for testing or small projects.
- **Starter Plan**: Up to 500 requests per minute, designed for small to medium applications.
- **Pro Plan**: Up to 2,000 requests per minute, for growing applications with moderate traffic.
- **Enterprise Plan**: Custom limits based on your needs, often 10,000+ requests per minute, for high-traffic or mission-critical applications.

To request a custom rate limit or discuss enterprise options, contact support via [community.aacsearch.com](https://community.aacsearch.com) or email support@aacsearch.com.

## Troubleshooting Rate Limit Issues

If you encounter issues related to rate limiting:

- **Frequent `429` Errors**: Review your application’s request patterns. Implement throttling or batching to reduce request frequency. Check if an upgrade to a higher plan is necessary.
- **Unexpected Limits**: Verify your plan details and API key permissions in the dashboard. If the limits shown in response headers don’t match your plan, contact support.
- **Retry Logic Failures**: Ensure your retry mechanism respects the `Retry-After` header and includes a maximum retry limit to prevent infinite loops.
- **API Usage Spikes**: Use the [Analytics API](../../api/analytics.md) to identify usage spikes. Adjust application behavior or infrastructure to handle peak loads better.
- **Contact Support**: For persistent issues or to request temporary limit increases for specific events (e.g., product launches), reach out to our support team.

## Additional Resources

- [AACSearch Dashboard](https://dashboard.aacsearch.com) - Monitor rate limit usage and upgrade plans.
- [API Quickstart](../../api/quickstart.md) - Quick reference for getting started with API integration.
- [Analytics API](../../api/analytics.md) - Track API usage to identify and mitigate rate limit issues.
- [Objects API](../../api/objects.md) - Learn about batch operations to reduce request count.
- [Caching Strategies](../performance/caching.md) - Implement caching to minimize API calls.
- [Community Forum](https://community.aacsearch.com) - Connect with other developers for rate limiting tips and solutions.
