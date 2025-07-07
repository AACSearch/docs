# Objects API

The Objects API allows you to manage the data within your AACSearch indexes. Objects are the individual records or documents that you store in an index for searching. This API provides endpoints to add, update, and delete objects.

## Overview

Objects represent the searchable content in your indexes. Using the Objects API, you can populate your indexes with data, update existing records, and remove outdated or irrelevant content.

- **Base Endpoint**: `/indexes/{name}/objects`
- **Authentication**: Requires an API key passed in the header as `X-API-Key`.

## Add Objects

Add new objects to an index for searching.

- **Endpoint**: `POST /indexes/{name}/objects`
- **Description**: Adds one or more objects to the specified index. Each object must have a unique `id` field to identify it within the index.

### Request (Single Object)

```bash
curl -X POST "https://api.aacsearch.com/indexes/products/objects" \
  -H "X-API-Key: your-api-key" \
  -H "Content-Type: application/json" \
  -d '{"id": "1", "title": "Smartphone Model X", "description": "Latest model with advanced features.", "category": "electronics", "price": 699.99}'
```

### Response (Single Object)

```json
{
  "id": "1",
  "index": "products",
  "status": "added",
  "details": {
    "title": "Smartphone Model X",
    "description": "Latest model with advanced features.",
    "category": "electronics",
    "price": 699.99
  }
}
```

### Request (Batch of Objects)

You can add multiple objects in a single request by sending an array:

```bash
curl -X POST "https://api.aacsearch.com/indexes/products/objects" \
  -H "X-API-Key: your-api-key" \
  -H "Content-Type: application/json" \
  -d '[
    {"id": "2", "title": "Smartphone Model Y", "description": "Affordable smartphone with great performance.", "category": "electronics", "price": 399.99},
    {"id": "3", "title": "Smartphone Model Z", "description": "Premium smartphone with cutting-edge technology.", "category": "electronics", "price": 999.99}
  ]'
```

### Response (Batch of Objects)

```json
{
  "index": "products",
  "status": "batch_added",
  "count": 2,
  "objectIDs": ["2", "3"]
}
```

## Update Objects

Update existing objects in an index.

- **Endpoint**: `PUT /indexes/{name}/objects/{id}`
- **Description**: Updates the specified object in the index. Only the provided fields will be updated; omitted fields remain unchanged.

### Request

```bash
curl -X PUT "https://api.aacsearch.com/indexes/products/objects/1" \
  -H "X-API-Key: your-api-key" \
  -H "Content-Type: application/json" \
  -d '{"price": 749.99, "description": "Updated model with enhanced features."}'
```

### Response

```json
{
  "id": "1",
  "index": "products",
  "status": "updated",
  "details": {
    "price": 749.99,
    "description": "Updated model with enhanced features."
  }
}
```

## Delete Objects

Remove objects from an index.

- **Endpoint**: `DELETE /indexes/{name}/objects/{id}`
- **Description**: Deletes the specified object from the index.

### Request

```bash
curl -X DELETE "https://api.aacsearch.com/indexes/products/objects/1" \
  -H "X-API-Key: your-api-key"
```

### Response

```json
{
  "id": "1",
  "index": "products",
  "status": "deleted"
}
```

## Batch Operations

AACSearch supports batch operations for adding, updating, or deleting multiple objects in a single request to optimize performance.

- **Endpoint**: `POST /indexes/{name}/objects/batch`
- **Description**: Performs multiple operations (add, update, delete) on objects in a single request.

### Request (Batch Operations)

```bash
curl -X POST "https://api.aacsearch.com/indexes/products/objects/batch" \
  -H "X-API-Key: your-api-key" \
  -H "Content-Type: application/json" \
  -d '{
    "requests": [
      {"action": "addObject", "body": {"id": "4", "title": "Tablet Model A", "category": "electronics", "price": 299.99}},
      {"action": "updateObject", "body": {"id": "2", "price": 449.99}},
      {"action": "deleteObject", "body": {"id": "3"}}
    ]
  }'
```

### Response (Batch Operations)

```json
{
  "index": "products",
  "status": "batch_processed",
  "count": 3,
  "results": [
    { "id": "4", "action": "addObject", "status": "added" },
    { "id": "2", "action": "updateObject", "status": "updated" },
    { "id": "3", "action": "deleteObject", "status": "deleted" }
  ]
}
```

## Best Practices for Managing Objects

- **Unique IDs**: Ensure each object has a unique `id` to prevent overwriting existing data unintentionally.
- **Batch Operations**: Use batch requests for bulk operations to reduce the number of API calls and improve performance.
- **Data Structure**: Structure your objects consistently with fields that match the searchable and filterable attributes defined in your index settings. See [Settings API](./settings.md) for configuration details.
- **Incremental Updates**: For large datasets, update objects incrementally to avoid timeouts or rate limit issues.

## Troubleshooting

If you encounter issues with object management:

- Ensure your API key has the necessary permissions to add, update, or delete objects.
- Verify that object IDs are unique when adding new objects to avoid overwriting existing ones.
- Check the [API Errors](../troubleshooting/api-errors.md) section for specific error codes and solutions.
- Use [Debug Mode](../troubleshooting/debug.md) to get detailed logs for diagnosing issues.

## Additional Resources

- [AACSearch Dashboard](https://dashboard.aacsearch.com) - Manage objects visually through the dashboard.
- [API Playground](https://api.aacsearch.com/playground) - Test object management API calls interactively.
- [Index Management Guide](../guides/dashboard/indexes.md) - Learn how to manage data within indexes via the dashboard.
- [Settings API](./settings.md) - Detailed documentation on configuring searchable and filterable attributes.
