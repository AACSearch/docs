# Integration

Integrating AACSearch into your application or website is the final step to enable powerful search functionality for your users. This guide will walk you through the process of connecting AACSearch to your project using API keys and SDKs, allowing you to perform searches, display results, and enhance user experience with real-time search capabilities.

## Prerequisites

Before integrating AACSearch, ensure you have completed the following:

- **Account Setup**: You have an active AACSearch account. If not, follow the [Account Setup](../getting-started/account-setup.md) guide.
- **Index Creation**: You have created at least one index. If not, follow the [First Index](../getting-started/first-index.md) guide.
- **Data Upload**: You have uploaded data to your index. If not, follow the [Data Upload](../getting-started/data-upload.md) guide.
- **API Key**: You have generated an API key with appropriate permissions. See [Account Setup](../getting-started/account-setup.md) for generating API keys.
- **Access to Dashboard**: Log in to the [AACSearch Dashboard](https://dashboard.aacsearch.com) with your credentials to retrieve necessary information.

## Step 1: Choose Your Integration Method

AACSearch offers multiple ways to integrate search functionality based on your project needs and technical expertise:

1. **Direct API Integration**: Use RESTful API endpoints to interact with AACSearch programmatically. This method is ideal for custom implementations and full control over search behavior.
2. **SDKs and Libraries**: Use pre-built SDKs for popular programming languages and frameworks (e.g., JavaScript, Python, React, Vue) to simplify integration. This is recommended for faster development and ease of use.
3. **UI Components**: Leverage ready-made UI components for web frameworks like React or Vue to quickly add search interfaces without building from scratch.
4. **Plugins for CMS**: Use plugins for content management systems like WordPress or Shopify to integrate search without coding.

This guide focuses on Direct API Integration and SDK usage, as they are the most common approaches. For CMS plugins or specific framework integrations, refer to the [Integrations](../../integrations/README.md) section.

## Step 2: Set Up Authentication

All interactions with AACSearch require authentication via an API key:

1. **Retrieve Your API Key**: From the AACSearch Dashboard, navigate to "API Keys" under "Settings." Copy an existing key with the necessary permissions (e.g., read access for search operations).
   - **Note**: Treat your API key like a password. Do not expose it in client-side code for public applications. For web apps, use a backend proxy or secure key management. See [API Key Management](../security/api-keys.md) for security best practices.
2. **Include in Requests**: Add the API key to every request as a header:
   ```
   X-API-Key: your-api-key
   ```

## Step 3: Perform Your First Search with API

To test integration, make a simple search request to your index using the AACSearch API:

1. **Identify Your Index**: Note the name of the index you want to search (e.g., "products").
2. **Construct the Search Request**: Use the `GET /search` endpoint with query parameters for your search term and index name.
   - **Example using `curl`**:
     ```bash
     curl -X GET "https://api.aacsearch.com/search" \
       -H "X-API-Key: your-api-key" \
       -G \
       -d "q=smartphone" \
       -d "index=products"
     ```
   - **Expected Response** (simplified JSON):
     ```json
     {
       "hits": [
         {
           "id": "1",
           "title": "Smartphone Model X",
           "description": "Latest model with advanced features.",
           "category": "electronics",
           "price": 699.99
         },
         {
           "id": "2",
           "title": "Smartphone Model Y",
           "description": "Affordable smartphone with great performance.",
           "category": "electronics",
           "price": 399.99
         }
       ],
       "nbHits": 2,
       "page": 1,
       "nbPages": 1,
       "hitsPerPage": 20,
       "processingTimeMS": 2,
       "query": "smartphone"
     }
     ```
3. **Verify Response**: Ensure you receive a response with search results (`hits`). If you encounter errors (e.g., `401 Unauthorized`), check your API key and permissions. If no results are returned, confirm your index contains relevant data.

For detailed search parameters (e.g., filters, facets), refer to the [Search API](../../api/search.md) documentation.

## Step 4: Integrate with SDK (Optional)

Using an SDK can simplify API interactions by handling authentication, request formatting, and response parsing. AACSearch provides SDKs for multiple languages and frameworks:

1. **Install the SDK**: Choose the appropriate SDK for your project and install it.

   - **JavaScript SDK Example** (for Node.js or browser):
     Install via npm:
     ```bash
     npm install aacsearch-js
     ```
   - Initialize the client:

     ```javascript
     import AACSearch from "aacsearch-js";

     const client = new AACSearch({
       apiKey: "your-api-key",
       baseUrl: "https://api.aacsearch.com",
     });
     ```

2. **Perform a Search**:
   - Use the SDK to search your index:
     ```javascript
     client
       .search({
         index: "products",
         q: "smartphone",
       })
       .then((response) => {
         console.log(response.hits); // Array of search results
       })
       .catch((error) => {
         console.error("Search error:", error);
       });
     ```
3. **Explore SDK Features**: SDKs often include helper methods for common tasks like autocomplete, filtering, and pagination. See [SDK Documentation](../../sdk/installation.md) for full capabilities.

## Step 5: Build a Search UI

To make search results accessible to users, create a search interface:

1. **Basic Search Form**: Add a search input field to your application or website where users can type queries.
   - **HTML Example**:
     ```html
     <form id="search-form">
       <input
         type="text"
         id="search-input"
         placeholder="Search products..."
         autocomplete="off"
       />
       <button type="submit">Search</button>
     </form>
     <div id="search-results"></div>
     ```
2. **Handle User Input**: Capture the user’s query and send it to AACSearch via API or SDK.

   - **JavaScript Example** (using SDK):

     ```javascript
     document
       .getElementById("search-form")
       .addEventListener("submit", function (e) {
         e.preventDefault();
         const query = document.getElementById("search-input").value;
         client
           .search({
             index: "products",
             q: query,
           })
           .then((response) => {
             displayResults(response.hits);
           });
       });

     function displayResults(hits) {
       const resultsDiv = document.getElementById("search-results");
       resultsDiv.innerHTML = "";
       if (hits.length === 0) {
         resultsDiv.innerHTML = "<p>No results found.</p>";
         return;
       }
       const ul = document.createElement("ul");
       hits.forEach((hit) => {
         const li = document.createElement("li");
         li.innerHTML = `<strong>${hit.title}</strong> - ${hit.description} (${hit.category}, $${hit.price})`;
         ul.appendChild(li);
       });
       resultsDiv.appendChild(ul);
     }
     ```

3. **Enhance with Features**: Add autocomplete, filters, or pagination to improve usability. Refer to [Autocomplete](../search/autocomplete.md) and [Faceted Search](../search/facets.md) for advanced UI features.

## Step 6: Test Your Integration

Before deploying to production, thoroughly test your search integration:

1. **Test Various Queries**: Try different search terms, including edge cases (e.g., empty queries, special characters, long phrases) to ensure consistent results.
2. **Check Performance**: Verify that search responses are fast enough for your use case. If slow, optimize your index or queries. See [Query Optimization](../performance/queries.md).
3. **Validate Results**: Ensure returned results match expectations based on your data and search configuration. Adjust relevance settings if needed. See [Relevance Tuning](../search/relevance.md).
4. **Simulate User Behavior**: Test the full user journey from entering a query to viewing results to ensure a seamless experience.

## Best Practices for Integration

- **Secure API Keys**: Avoid exposing API keys in client-side code. Use environment variables or a backend proxy for secure key storage.
- **Handle Errors Gracefully**: Implement error handling for API failures (e.g., network issues, rate limits) and display user-friendly messages. See [API Errors](../../troubleshooting/api-errors.md).
- **Optimize for Speed**: Cache frequent search results if appropriate to reduce API calls and improve response time. See [Caching Strategies](../performance/caching.md).
- **Monitor Usage**: Track API usage and search analytics in the dashboard to identify bottlenecks or areas for improvement. See [Analytics & Insights](../dashboard/analytics.md).
- **Stay Within Rate Limits**: Be mindful of API rate limits to avoid disruptions. Batch requests or implement retry logic for `429 Too Many Requests` errors. See [Rate Limiting](../security/rate-limiting.md).

## Next Steps

With AACSearch integrated into your application, explore additional features to enhance search functionality:

- **[Search Configuration](../dashboard/search-config.md)**: Fine-tune search settings like relevance, synonyms, and typo tolerance for better results.
- **[Autocomplete](../search/autocomplete.md)**: Add real-time suggestions as users type to improve search usability.
- **[Analytics & Insights](../dashboard/analytics.md)**: Use search analytics to understand user behavior and optimize performance.
- **[Advanced Topics](../../advanced/README.md)**: Dive into machine learning, vector search, and custom ranking for cutting-edge search capabilities.

## Troubleshooting

If you encounter issues during integration:

- **Authentication Errors**: If you receive a `401 Unauthorized` error, verify your API key is correct and has the necessary permissions. Generate a new key if needed.
- **No Results Returned**: Ensure your index contains data and the query matches the content. Check searchable attributes in your index settings.
- **Slow Response Times**: Optimize your queries or index configuration. Large datasets or complex filters can impact speed. See [Query Optimization](../performance/queries.md).
- **SDK Installation Issues**: If an SDK fails to install or work, check for version compatibility with your project or reinstall dependencies. Refer to [SDK Troubleshooting](../../troubleshooting/sdk.md).
- **Contact Support**: For further assistance, reach out to our support team via [community.aacsearch.com](https://community.aacsearch.com) or email support@aacsearch.com.

## Additional Resources

- [AACSearch Dashboard](https://dashboard.aacsearch.com) - Manage API keys and monitor integration.
- [API Quickstart](../../api/quickstart.md) - Quick reference for getting started with API integration.
- [Search API Reference](../../api/search.md) - Detailed documentation on search parameters and responses.
- [SDK Documentation](../../sdk/installation.md) - Guides for installing and using AACSearch SDKs.
- [Community Forum](https://community.aacsearch.com) - Connect with other developers for integration tips and solutions.
