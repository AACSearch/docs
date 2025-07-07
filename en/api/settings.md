# Settings API

The Settings API allows you to configure search parameters and behaviors for your AACSearch indexes. This API provides endpoints to customize how search results are ranked, filtered, and displayed to optimize the search experience for your users.

## Overview

Index settings control various aspects of search functionality, such as which attributes are searchable, how results are ranked, and how typos are handled. The Settings API enables you to fine-tune these parameters to match your specific use case.

- **Base Endpoint**: `/indexes/{name}/settings`
- **Authentication**: Requires an API key passed in the header as `X-API-Key`.

## Get Index Settings

Retrieve the current settings for a specific index.

- **Endpoint**: `GET /indexes/{name}/settings`
- **Description**: Returns the complete configuration of settings for the specified index.

### Request

```bash
curl -X GET "https://api.aacsearch.com/indexes/products/settings" \
  -H "X-API-Key: your-api-key"
```

### Response

```json
{
  "index": "products",
  "settings": {
    "searchableAttributes": ["title", "description", "brand"],
    "filterableAttributes": ["category", "price", "brand"],
    "sortableAttributes": ["price", "rating"],
    "ranking": ["words", "typo", "geo", "filters", "exact", "custom"],
    "customRanking": ["desc(price)"],
    "typoTolerance": {
      "enabled": true,
      "minWordSizeForTypos": {
        "oneTypo": 4,
        "twoTypos": 8
      }
    },
    "faceting": {
      "maxValuesPerFacet": 100
    },
    "pagination": {
      "hitsPerPage": 20
    },
    "highlighting": {
      "attributesToHighlight": ["title", "description"],
      "highlightPreTag": "<em>",
      "highlightPostTag": "</em>"
    },
    "synonyms": true,
    "queryLanguages": ["en"]
  },
  "updatedAt": "2023-01-05T10:20:30Z"
}
```

## Update Index Settings

Update the settings for a specific index to customize search behavior.

- **Endpoint**: `PUT /indexes/{name}/settings`
- **Description**: Updates the settings for the specified index. Only the provided fields will be updated; omitted fields remain unchanged.

### Request

```bash
curl -X PUT "https://api.aacsearch.com/indexes/products/settings" \
  -H "X-API-Key: your-api-key" \
  -H "Content-Type: application/json" \
  -d '{
    "searchableAttributes": ["title", "description", "brand", "category"],
    "filterableAttributes": ["category", "price", "brand", "availability"],
    "sortableAttributes": ["price", "rating", "releaseDate"],
    "ranking": ["words", "typo", "geo", "filters", "exact", "custom"],
    "customRanking": ["desc(price)", "desc(rating)"],
    "typoTolerance": {
      "enabled": true,
      "minWordSizeForTypos": {
        "oneTypo": 3,
        "twoTypos": 7
      }
    },
    "faceting": {
      "maxValuesPerFacet": 50
    },
    "pagination": {
      "hitsPerPage": 25
    },
    "highlighting": {
      "attributesToHighlight": ["title", "description", "brand"],
      "highlightPreTag": "<strong>",
      "highlightPostTag": "</strong>"
    },
    "queryLanguages": ["en", "fr"]
  }'
```

### Response

```json
{
  "index": "products",
  "status": "updated",
  "updatedAt": "2023-01-05T10:25:45Z",
  "settings": {
    "searchableAttributes": ["title", "description", "brand", "category"],
    "filterableAttributes": ["category", "price", "brand", "availability"],
    "sortableAttributes": ["price", "rating", "releaseDate"],
    "ranking": ["words", "typo", "geo", "filters", "exact", "custom"],
    "customRanking": ["desc(price)", "desc(rating)"],
    "typoTolerance": {
      "enabled": true,
      "minWordSizeForTypos": {
        "oneTypo": 3,
        "twoTypos": 7
      }
    },
    "faceting": {
      "maxValuesPerFacet": 50
    },
    "pagination": {
      "hitsPerPage": 25
    },
    "highlighting": {
      "attributesToHighlight": ["title", "description", "brand"],
      "highlightPreTag": "<strong>",
      "highlightPostTag": "</strong>"
    },
    "synonyms": true,
    "queryLanguages": ["en", "fr"]
  }
}
```

## Key Settings Parameters

The following are some of the most important settings you can configure through the Settings API:

- **`searchableAttributes`**: Defines which fields in your objects are searchable. List attributes in order of importance for ranking purposes. Example: `["title", "description"]`.
- **`filterableAttributes`**: Specifies which attributes can be used for filtering search results. Example: `["category", "price"]`.
- **`sortableAttributes`**: Defines attributes that can be used for sorting search results. Example: `["price", "rating"]`.
- **`ranking`**: Specifies the order of ranking criteria for search results. Common values include `words` (word matching), `typo` (typo tolerance), `geo` (geolocation), `filters` (applied filters), `exact` (exact matches), and `custom` (custom rules). Example: `["words", "typo", "geo", "filters", "exact", "custom"]`.
- **`customRanking`**: Custom ranking rules to prioritize certain attributes (e.g., `desc(price)` for descending price). Example: `["desc(price)", "asc(rating)"]`.
- **`typoTolerance`**: Controls how typos are handled in search queries. You can enable/disable it and set thresholds for when typos are tolerated. Example: `{"enabled": true, "minWordSizeForTypos": {"oneTypo": 4, "twoTypos": 8}}`.
- **`faceting`**: Configures facet behavior, such as the maximum number of values returned per facet. Example: `{"maxValuesPerFacet": 100}`.
- **`pagination`**: Sets pagination defaults, such as the number of hits per page. Example: `{"hitsPerPage": 20}`.
- **`highlighting`**: Configures how matching terms are highlighted in search results. Example: `{"attributesToHighlight": ["title"], "highlightPreTag": "<em>", "highlightPostTag": "</em>"}`.
- **`queryLanguages`**: Specifies the languages for query processing (e.g., for language-specific stemming or stop words). Example: `["en", "fr"]`.
- **`synonyms`**: Enables synonym support for the index. Set to `true` to enable. See [Synonyms](../guides/search/synonyms.md) for detailed configuration.

## Best Practices for Configuring Settings

- **Prioritize Searchable Attributes**: List the most important attributes first in `searchableAttributes` to influence ranking. For example, prioritize `title` over `description` if titles are more relevant to users.
- **Optimize Filtering**: Only include attributes in `filterableAttributes` that are necessary for filtering to reduce index size and improve performance.
- **Customize Ranking**: Use `ranking` and `customRanking` to tailor result ordering to your use case. For e-commerce, you might prioritize price or popularity with `customRanking: ["desc(popularity)"]`.
- **Handle Typos Appropriately**: Adjust `typoTolerance` based on your audience. For short queries, lower the `minWordSizeForTypos` thresholds; for precise searches, consider disabling it.
- **Test Settings Iteratively**: Update settings incrementally and monitor the impact on search relevance and performance using the [Analytics API](./analytics.md).

## Troubleshooting

If you encounter issues with index settings:

- Ensure your API key has the necessary permissions to update settings.
- Verify that the settings you are updating are compatible with your data structure (e.g., attributes listed in `searchableAttributes` must exist in your objects).
- Check the [API Errors](../troubleshooting/api-errors.md) section for specific error codes and solutions.
- Use [Debug Mode](../troubleshooting/debug.md) to get detailed logs for diagnosing issues.

## Additional Resources

- [AACSearch Dashboard](https://dashboard.aacsearch.com) - Configure settings visually through the dashboard.
- [API Playground](https://api.aacsearch.com/playground) - Test settings API calls interactively.
- [Search Configuration Guide](../guides/dashboard/search-config.md) - Learn how to configure search settings via the dashboard.
- [Relevance Tuning](../guides/search/relevance.md) - Detailed guide on optimizing search relevance with settings.
- [Analytics API](./analytics.md) - Use analytics to evaluate the impact of settings changes.
