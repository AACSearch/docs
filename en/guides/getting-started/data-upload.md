# Data Upload

Uploading data to your AACSearch index is the next step after creating it. This process allows you to populate your index with the content you want to make searchable. This guide will walk you through the steps to upload data to your index using the AACSearch Dashboard and provide an overview of using the API for more advanced or automated uploads.

## Prerequisites

Before uploading data, ensure you have completed the following:

- **Account Setup**: You have an active AACSearch account. If not, follow the [Account Setup](../getting-started/account-setup.md) guide.
- **Index Creation**: You have created at least one index. If not, follow the [First Index](../getting-started/first-index.md) guide.
- **Access to Dashboard**: Log in to the [AACSearch Dashboard](https://dashboard.aacsearch.com) with your credentials.

## Step 1: Prepare Your Data

Before uploading, ensure your data is formatted correctly for AACSearch:

1. **Structure Your Data**: AACSearch expects data in JSON format, where each item (or "object") in your index is a JSON object with a unique `id` field. Other fields can represent the searchable content (e.g., `title`, `description`, `category`).
   - **Example Single Object**:
     ```json
     {
       "id": "1",
       "title": "Smartphone Model X",
       "description": "Latest model with advanced features.",
       "category": "electronics",
       "price": 699.99
     }
     ```
   - **Example Array of Objects** (for batch upload):
     ```json
     [
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
     ]
     ```
2. **Ensure Unique IDs**: Each object must have a unique `id` to prevent overwriting existing data. If an `id` already exists in the index, uploading an object with the same `id` will update the existing record.
3. **Match Schema (Optional)**: If you’ve defined searchable or filterable attributes in your index settings, ensure your data includes those fields for optimal search performance. See [Search Configuration](../dashboard/search-config.md) for details.

## Step 2: Upload Data via Dashboard

The AACSearch Dashboard provides a user-friendly way to upload small to medium datasets manually:

1. **Navigate to Indexes**: On the left-hand sidebar of the dashboard, click on "Indexes" to view your list of indexes.
2. **Select Your Index**: Click on the index you want to upload data to. This opens the index details page.
3. **Go to Data Management**: Look for a tab or section labeled "Data," "Objects," or "Upload Data" (the exact name may vary based on your dashboard version).
4. **Upload Data**:
   - **Manual Entry**: For small datasets, you can manually enter a single JSON object or paste a JSON array directly into a provided text field.
   - **File Upload**: For larger datasets, click "Upload File" and select a JSON file from your computer. Ensure the file contains a valid JSON array of objects as shown in the example above.
5. **Validate and Confirm**: AACSearch will validate your data for formatting errors. If there are issues (e.g., missing `id` fields), you’ll see error messages with details. Correct any errors and retry. If valid, click "Upload" or "Add Objects" to add the data to your index.
6. **Check Upload Status**: After uploading, the dashboard will display the number of objects in your index. Refresh the page if the count doesn’t update immediately.

## Step 3: Verify Data in Index

To confirm your data has been uploaded successfully:

1. **View Object Count**: On the index details page, check the total number of objects. It should reflect the number of items you uploaded.
2. **Browse Data**: Some dashboards allow you to browse or preview the uploaded objects. Look for a "Browse" or "Data View" option to see a sample of your data.
3. **Test Search**: Use the dashboard’s search preview feature (if available) to test searching within your index. Enter a query to ensure results are returned as expected.

## Alternative: Upload Data via API

For larger datasets, automated workflows, or integration with existing systems, uploading data via the AACSearch API is more efficient:

1. **Obtain API Key**: Ensure you have an API key with permissions to add objects. See [Account Setup](../getting-started/account-setup.md) for generating API keys.
2. **Use Objects API**: Use the `POST /indexes/{name}/objects` endpoint to add data. You can upload a single object or a batch of objects in one request.
   - **Single Object Example** (using `curl`):
     ```bash
     curl -X POST "https://api.aacsearch.com/indexes/products/objects" \
       -H "X-API-Key: your-api-key" \
       -H "Content-Type: application/json" \
       -d '{"id": "1", "title": "Smartphone Model X", "description": "Latest model with advanced features.", "category": "electronics", "price": 699.99}'
     ```
   - **Batch Upload Example**:
     ```bash
     curl -X POST "https://api.aacsearch.com/indexes/products/objects" \
       -H "X-API-Key: your-api-key" \
       -H "Content-Type: application/json" \
       -d '[{"id": "1", "title": "Smartphone Model X", "description": "Latest model with advanced features.", "category": "electronics", "price": 699.99}, {"id": "2", "title": "Smartphone Model Y", "description": "Affordable smartphone with great performance.", "category": "electronics", "price": 399.99}]'
     ```
3. **Check Response**: The API will return a response confirming the upload status, including the `id` of added objects or error messages if the upload fails.
4. **Automate with Scripts**: For recurring uploads, script the process using your preferred programming language (e.g., Python, Node.js) with the AACSearch SDK or direct API calls. See [SDK Documentation](../../sdk/installation.md) for SDK setup.

## Best Practices for Data Upload

- **Batch Uploads for Efficiency**: When uploading large datasets, send data in batches (e.g., 100-1000 objects per request) to avoid timeouts and reduce API calls. Check AACSearch rate limits in [Rate Limiting](../security/rate-limiting.md).
- **Validate Data Before Upload**: Ensure your JSON is valid and all required fields (especially `id`) are present to prevent upload failures.
- **Incremental Updates**: For existing indexes, upload only new or updated objects to avoid unnecessary processing. Use the API’s update functionality to modify existing records by `id`.
- **Monitor Index Size**: Be aware of your plan’s limits on index size or object count. If approaching limits, consider upgrading your plan or optimizing data. See [Billing](../dashboard/billing.md) for plan details.

## Next Steps

With data uploaded to your index, you’re ready to integrate search functionality into your application or website:

- **[Integration](../getting-started/integration.md)**: Learn how to connect AACSearch to your application for real-time search.
- **[Search Configuration](../dashboard/search-config.md)**: Fine-tune search settings to improve relevance and user experience.
- **[Analytics & Insights](../dashboard/analytics.md)**: Monitor how users interact with your search to identify areas for improvement.

## Troubleshooting

If you encounter issues while uploading data:

- **JSON Format Errors**: Ensure your data is valid JSON. Use a JSON validator tool to check for syntax errors like missing commas or brackets.
- **Missing ID Field**: Every object must have a unique `id`. If missing, AACSearch will reject the upload. Add `id` fields and retry.
- **File Size Limits**: If uploading via the dashboard, check for file size restrictions. For large files, split data into smaller chunks or use the API.
- **Rate Limit Exceeded**: If using the API and receiving a `429 Too Many Requests` error, you’ve hit rate limits. Wait before retrying or batch uploads more efficiently. See [Rate Limiting](../security/rate-limiting.md).
- **Contact Support**: For further assistance, reach out to our support team via [community.aacsearch.com](https://community.aacsearch.com) or email support@aacsearch.com.

## Additional Resources

- [AACSearch Dashboard](https://dashboard.aacsearch.com) - Upload and manage data visually.
- [Objects API Reference](../../api/objects.md) - Detailed documentation on uploading data via API.
- [SDK Documentation](../../sdk/installation.md) - Use SDKs for easier API integration in various programming languages.
- [Community Forum](https://community.aacsearch.com) - Connect with other users for tips and troubleshooting.
