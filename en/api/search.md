# Search API

The Search API is the core of AACSearch, allowing you to perform search queries across your indexes. This documentation provides detailed information on how to use the Search API to retrieve relevant results for your users.

## Overview

The Search API endpoint enables you to search for objects within a specific index. You can customize the search with various parameters to filter, sort, and refine the results.

- **Endpoint**: `GET /search`
- **Authentication**: Requires an API key passed in the header as `X-API-Key`.

## Basic Search Request

To perform a basic search, you need to specify the search query and the index to search in. Here's an example:

```bash
curl -X GET "https://api.aacsearch.com/search" \
  -H "X-API-Key: your-api-key" \
  -G \
  -d "q=smartphone" \
  -d "index=products"
```

### Response

A successful search request returns a JSON response with the search results:

```json
{
  "hits": [
    {
      "id": "123",
      "title": "Smartphone Model X",
      "description": "Latest model with advanced features.",
      "category": "electronics",
      "price": 699.99
    },
    {
      "id": "124",
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
  "processingTimeMS": 3,
  "query": "smartphone",
  "params": "q=smartphone&index=products"
}
```

## Search Parameters

The Search API supports a variety of parameters to refine your search results. Below are the most commonly used parameters:

- **`q`**: The search query string. This is the text that users are searching for. Example: `q=smartphone`.
- **`index`**: The name of the index to search in. Example: `index=products`.
- **`filters`**: Filters to apply to the search results. Filters are used to narrow down results based on specific criteria. Example: `filters=category:electronics AND price:100 TO 1000`.
- **`facets`**: Facets for aggregation, allowing you to retrieve counts of results for specific categories or values. Example: `facets=brand,price`.
- **`attributesToRetrieve`**: Specifies which fields of the objects to return in the results. Example: `attributesToRetrieve=title,description,price`.
- **`attributesToHighlight`**: Fields to highlight in the search results (e.g., matching search terms). Example: `attributesToHighlight=title,description`.
- **`page`**: The page number for pagination. Example: `page=2`.
- **`hitsPerPage`**: The number of results per page. Default is 20. Example: `hitsPerPage=10`.
- **`sortBy`**: Sort the results by a specific field. Example: `sortBy=price:asc` for ascending order by price.

### Example with Parameters

Here's an example of a search request with multiple parameters:

```bash
curl -X GET "https://api.aacsearch.com/search" \
  -H "X-API-Key: your-api-key" \
  -G \
  -d "q=smartphone" \
  -d "index=products" \
  -d "filters=category:electronics AND price:100 TO 1000" \
  -d "facets=brand,price" \
  -d "attributesToRetrieve=title,description,price" \
  -d "attributesToHighlight=title" \
  -d "page=1" \
  -d "hitsPerPage=5" \
  -d "sortBy=price:desc"
```

### Response with Facets

When facets are requested, the response includes facet counts:

```json
{
  "hits": [
    {
      "id": "123",
      "title": "<em>Smartphone</em> Model X",
      "description": "Latest model with advanced features.",
      "price": 699.99
    }
    // ... more hits
  ],
  "nbHits": 5,
  "page": 1,
  "nbPages": 1,
  "hitsPerPage": 5,
  "processingTimeMS": 4,
  "query": "smartphone",
  "params": "q=smartphone&index=products&filters=category:electronics AND price:100 TO 1000&facets=brand,price&attributesToRetrieve=title,description,price&attributesToHighlight=title&page=1&hitsPerPage=5&sortBy=price:desc",
  "facets": {
    "brand": {
      "BrandA": 2,
      "BrandB": 3
    },
    "price": {
      "100-500": 2,
      "501-1000": 3
    }
  }
}
```

## Advanced Search Features

### Typo Tolerance

AACSearch automatically handles typos in search queries. You can configure typo tolerance settings via the [Settings API](./settings.md).

### Synonyms

AACSearch supports synonyms to improve search relevance. For example, searching for "phone" can return results for "smartphone" if synonyms are configured. See [Synonyms](../guides/search/synonyms.md) for setup instructions.

### Relevance Tuning

You can customize how results are ranked using relevance tuning. Learn more in [Relevance Tuning](../guides/search/relevance.md).

## Rate Limits

Be aware of rate limits when using the Search API. If you exceed the limit, you'll receive a `429 Too Many Requests` error. For details on rate limiting, see [Rate Limiting](../guides/security/rate-limiting.md).

## Troubleshooting

If you encounter issues with search results:

- Verify that your index contains the expected data.
- Check your filters and parameters for typos or incorrect syntax.
- Review the [API Errors](../troubleshooting/api-errors.md) section for specific error codes.
- Enable debug mode for detailed logs as described in [Debug Mode](../troubleshooting/debug.md).

## Additional Resources

- [AACSearch Dashboard](https://dashboard.aacsearch.com) - Manage your indexes and view search analytics.
- [API Playground](https://api.aacsearch.com/playground) - Test search queries interactively.
- [Search Configuration](../guides/dashboard/search-config.md) - Customize search behavior via the dashboard.
