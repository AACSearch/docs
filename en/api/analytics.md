# Analytics API

The Analytics API provides access to usage statistics and insights for your AACSearch indexes. This API allows you to retrieve data on search performance, user behavior, and other metrics to optimize your search experience.

## Overview

Analytics data helps you understand how users interact with your search functionality, identify popular queries, and detect areas for improvement in your indexes. The Analytics API offers endpoints to fetch detailed reports and metrics.

- **Base Endpoint**: `/analytics`
- **Authentication**: Requires an API key passed in the header as `X-API-Key`.

## Get Analytics Overview

Retrieve a summary of analytics for your AACSearch account.

- **Endpoint**: `GET /analytics`
- **Description**: Returns an overview of key metrics across all indexes, such as total searches, average response time, and popular queries.

### Request

```bash
curl -X GET "https://api.aacsearch.com/analytics" \
  -H "X-API-Key: your-api-key"
```

### Response

```json
{
  "overview": {
    "totalSearches": 12500,
    "averageResponseTimeMS": 12,
    "searchSuccessRate": 98.5,
    "totalIndexes": 3,
    "totalObjects": 4500
  },
  "popularQueries": [
    {
      "query": "smartphone",
      "count": 1500,
      "lastUsed": "2023-01-10T14:30:00Z"
    },
    { "query": "laptop", "count": 1200, "lastUsed": "2023-01-09T10:15:00Z" },
    { "query": "headphones", "count": 800, "lastUsed": "2023-01-08T09:45:00Z" }
  ],
  "period": {
    "start": "2023-01-01T00:00:00Z",
    "end": "2023-01-10T23:59:59Z"
  }
}
```

## Get Index-Specific Analytics

Retrieve detailed analytics for a specific index.

- **Endpoint**: `GET /analytics/index/{name}`
- **Description**: Returns metrics and insights for the specified index, including search volume, query performance, and facet usage.

### Request

```bash
curl -X GET "https://api.aacsearch.com/analytics/index/products" \
  -H "X-API-Key: your-api-key" \
  -G \
  -d "startDate=2023-01-01" \
  -d "endDate=2023-01-10"
```

### Response

```json
{
  "index": "products",
  "metrics": {
    "totalSearches": 8000,
    "averageResponseTimeMS": 10,
    "searchSuccessRate": 99.0,
    "totalObjects": 3000,
    "noResultRate": 5.2
  },
  "popularQueries": [
    { "query": "smartphone", "count": 1000, "noResults": 50 },
    { "query": "tablet", "count": 600, "noResults": 30 }
  ],
  "popularFilters": [
    { "filter": "category:electronics", "count": 2500 },
    { "filter": "price:100 TO 500", "count": 1800 }
  ],
  "popularFacets": [
    { "facet": "brand", "count": 2000 },
    { "facet": "price", "count": 1500 }
  ],
  "period": {
    "start": "2023-01-01T00:00:00Z",
    "end": "2023-01-10T23:59:59Z"
  }
}
```

## Get Query Performance Report

Retrieve a detailed report on query performance to identify slow or problematic searches.

- **Endpoint**: `GET /analytics/queries`
- **Description**: Returns a list of queries with performance metrics like response time and success rate. You can filter by index and date range.

### Request

```bash
curl -X GET "https://api.aacsearch.com/analytics/queries" \
  -H "X-API-Key: your-api-key" \
  -G \
  -d "index=products" \
  -d "startDate=2023-01-01" \
  -d "endDate=2023-01-10" \
  -d "sortBy=responseTime:desc" \
  -d "limit=5"
```

### Response

```json
{
  "queries": [
    {
      "query": "smartphone 5g ultra premium",
      "count": 100,
      "averageResponseTimeMS": 25,
      "successRate": 95.0,
      "noResults": 10
    },
    {
      "query": "gaming laptop high performance",
      "count": 80,
      "averageResponseTimeMS": 22,
      "successRate": 97.5,
      "noResults": 5
    },
    {
      "query": "wireless headphones noise cancelling",
      "count": 120,
      "averageResponseTimeMS": 20,
      "successRate": 98.3,
      "noResults": 3
    },
    {
      "query": "budget smartphone under 200",
      "count": 150,
      "averageResponseTimeMS": 18,
      "successRate": 96.7,
      "noResults": 8
    },
    {
      "query": "tablet for kids",
      "count": 90,
      "averageResponseTimeMS": 15,
      "successRate": 99.0,
      "noResults": 2
    }
  ],
  "index": "products",
  "period": {
    "start": "2023-01-01T00:00:00Z",
    "end": "2023-01-10T23:59:59Z"
  },
  "totalQueries": 2500,
  "averageResponseTimeMS": 18.5
}
```

## Parameters for Analytics Requests

The Analytics API supports various parameters to customize the data you retrieve:

- **`startDate`**: The start date for the analytics period (ISO 8601 format). Example: `startDate=2023-01-01`.
- **`endDate`**: The end date for the analytics period (ISO 8601 format). Example: `endDate=2023-01-10`.
- **`index`**: Filter analytics by a specific index. Example: `index=products`.
- **`sortBy`**: Sort results by a specific metric (e.g., `responseTime:desc` for descending response time). Example: `sortBy=count:desc`.
- **`limit`**: Limit the number of results returned. Default is 10. Example: `limit=5`.

## Best Practices for Using Analytics

- **Regular Monitoring**: Check analytics regularly to identify trends in user behavior and search performance.
- **Optimize Slow Queries**: Use query performance reports to find slow or unsuccessful searches and adjust index settings or data structure accordingly. See [Settings API](./settings.md) for optimization options.
- **Focus on No-Result Queries**: Analyze queries with high no-result rates to improve data coverage or suggest synonyms. See [Synonyms](../guides/search/synonyms.md) for setup instructions.
- **Custom Reports**: Use date range parameters to create custom reports for specific campaigns or time periods.

## Troubleshooting

If you encounter issues with analytics data:

- Ensure your API key has the necessary permissions to access analytics.
- Verify that the date range and index parameters are correct.
- Check the [API Errors](../troubleshooting/api-errors.md) section for specific error codes and solutions.
- Use [Debug Mode](../troubleshooting/debug.md) to get detailed logs for diagnosing issues.

## Additional Resources

- [AACSearch Dashboard](https://dashboard.aacsearch.com) - View analytics visually through the dashboard.
- [API Playground](https://api.aacsearch.com/playground) - Test analytics API calls interactively.
- [Analytics & Insights Guide](../guides/dashboard/analytics.md) - Learn how to interpret analytics data via the dashboard.
- [Search Configuration](../guides/dashboard/search-config.md) - Adjust search settings based on analytics insights.
