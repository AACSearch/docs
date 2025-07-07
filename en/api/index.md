# Index API

The Index API allows you to manage search indexes in AACSearch. Indexes are containers for your searchable data, and this API provides endpoints to create, update, delete, and list indexes.

## Overview

Indexes are the fundamental structure in AACSearch where your data is stored and searched. The Index API provides full control over index management, enabling you to organize your data effectively.

- **Base Endpoint**: `/indexes`
- **Authentication**: Requires an API key passed in the header as `X-API-Key`.

## List Indexes

Retrieve a list of all indexes in your AACSearch account.

- **Endpoint**: `GET /indexes`
- **Description**: Returns a list of index names and basic metadata.

### Request

```bash
curl -X GET "https://api.aacsearch.com/indexes" \
  -H "X-API-Key: your-api-key"
```

### Response

```json
{
  "indexes": [
    {
      "name": "products",
      "createdAt": "2023-01-01T00:00:00Z",
      "updatedAt": "2023-01-02T00:00:00Z",
      "entries": 1500
    },
    {
      "name": "content",
      "createdAt": "2023-01-03T00:00:00Z",
      "updatedAt": "2023-01-03T00:00:00Z",
      "entries": 500
    }
  ],
  "total": 2
}
```

## Create an Index

Create a new index to store and search data.

- **Endpoint**: `POST /indexes`
- **Description**: Creates a new index with the specified name and optional settings.

### Request

```bash
curl -X POST "https://api.aacsearch.com/indexes" \
  -H "X-API-Key: your-api-key" \
  -H "Content-Type: application/json" \
  -d '{"name": "products", "settings": {"searchableAttributes": ["title", "description"], "filterableAttributes": ["category", "price"]}}'
```

### Response

```json
{
  "name": "products",
  "createdAt": "2023-01-01T00:00:00Z",
  "updatedAt": "2023-01-01T00:00:00Z",
  "entries": 0,
  "settings": {
    "searchableAttributes": ["title", "description"],
    "filterableAttributes": ["category", "price"]
  },
  "status": "created"
}
```

## Update an Index

Update the settings or metadata of an existing index.

- **Endpoint**: `PUT /indexes/{name}`
- **Description**: Updates the settings of the specified index.

### Request

```bash
curl -X PUT "https://api.aacsearch.com/indexes/products" \
  -H "X-API-Key: your-api-key" \
  -H "Content-Type: application/json" \
  -d '{"settings": {"searchableAttributes": ["title", "description", "brand"], "filterableAttributes": ["category", "price", "brand"]}}'
```

### Response

```json
{
  "name": "products",
  "createdAt": "2023-01-01T00:00:00Z",
  "updatedAt": "2023-01-02T00:00:00Z",
  "entries": 1500,
  "settings": {
    "searchableAttributes": ["title", "description", "brand"],
    "filterableAttributes": ["category", "price", "brand"]
  },
  "status": "updated"
}
```

## Delete an Index

Remove an index and all its data from AACSearch.

- **Endpoint**: `DELETE /indexes/{name}`
- **Description**: Deletes the specified index and all associated data. This action is irreversible.

### Request

```bash
curl -X DELETE "https://api.aacsearch.com/indexes/products" \
  -H "X-API-Key: your-api-key"
```

### Response

```json
{
  "name": "products",
  "status": "deleted"
}
```

## Best Practices for Index Management

- **Naming Conventions**: Use descriptive names for indexes that reflect the type of data they contain (e.g., "products", "users", "content").
- **Settings Configuration**: Configure searchable and filterable attributes based on your data structure to optimize search performance. See [Settings API](./settings.md) for advanced configuration options.
- **Data Organization**: Consider creating separate indexes for different types of data or use cases to improve search relevance and performance.
- **Regular Updates**: Periodically update index settings to reflect changes in your data or search requirements.

## Troubleshooting

If you encounter issues with index management:

- Ensure your API key has the necessary permissions to create, update, or delete indexes.
- Verify that the index name is unique when creating a new index.
- Check the [API Errors](../troubleshooting/api-errors.md) section for specific error codes and solutions.
- Use [Debug Mode](../troubleshooting/debug.md) to get detailed logs for diagnosing issues.

## Additional Resources

- [AACSearch Dashboard](https://dashboard.aacsearch.com) - Manage indexes visually through the dashboard.
- [API Playground](https://api.aacsearch.com/playground) - Test index management API calls interactively.
- [Index Management Guide](../guides/dashboard/indexes.md) - Learn how to manage indexes via the dashboard.
- [Settings API](./settings.md) - Detailed documentation on configuring index settings.
