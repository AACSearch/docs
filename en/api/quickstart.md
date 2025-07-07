# API Quickstart Guide

Welcome to the AACSearch API Quickstart Guide. This guide will help you get started with the AACSearch API, allowing you to integrate powerful search capabilities into your applications quickly.

## Prerequisites

Before you begin, ensure you have the following:

- An AACSearch account. If you don't have one, sign up at [AACSearch Dashboard](https://dashboard.aacsearch.com).
- An API key. You can generate this from your dashboard under the "API Keys" section.

## Making Your First API Call

Follow these steps to make your first API call to AACSearch:

1. **Set Up Your Environment**: Ensure you have a tool or library to make HTTP requests. This could be `curl` for command-line requests, Postman for a GUI, or a library in your programming language of choice (e.g., `axios` for JavaScript, `requests` for Python).

2. **Prepare Your API Key**: Keep your API key handy. You'll need to include it in the header of your requests as `X-API-Key`.

3. **Make a Simple Search Request**: Let's start with a basic search query. Replace `your-api-key` with your actual API key in the command below:

   ```bash
   curl -X GET "https://api.aacsearch.com/search" \
     -H "X-API-Key: your-api-key" \
     -G \
     -d "q=example" \
     -d "index=my-index"
   ```

   This command searches for the term "example" in the index named "my-index". If the index doesn't exist yet, you'll need to create one via the dashboard or API.

4. **Interpret the Response**: If successful, you'll receive a JSON response like this:

   ```json
   {
     "hits": [],
     "nbHits": 0,
     "page": 1,
     "nbPages": 0,
     "hitsPerPage": 20,
     "processingTimeMS": 1,
     "query": "example",
     "params": "q=example&index=my-index"
   }
   ```

   Since no data exists yet, the `hits` array is empty. Once you add data to your index, you'll see search results here.

## Next Steps

- **Create an Index**: Use the dashboard or the API to create a search index. Here's how to do it via API:

  ```bash
  curl -X POST "https://api.aacsearch.com/indexes" \
    -H "X-API-Key: your-api-key" \
    -H "Content-Type: application/json" \
    -d '{"name": "my-index"}'
  ```

- **Add Data**: Upload data to your index for searching:

  ```bash
  curl -X POST "https://api.aacsearch.com/indexes/my-index/objects" \
    -H "X-API-Key: your-api-key" \
    -H "Content-Type: application/json" \
    -d '{"id": "1", "title": "Example Item", "description": "This is an example item for search."}'
  ```

- **Explore More Endpoints**: Check out the full [API Reference](../api/search.md) for details on search parameters, index management, and more.

## Troubleshooting

If you encounter issues:

- Ensure your API key is correct and has the necessary permissions.
- Check the [API Errors](../troubleshooting/api-errors.md) section for common error codes and solutions.
- Contact support via the [Community Forum](https://community.aacsearch.com) if problems persist.

## Additional Resources

- [AACSearch Dashboard](https://dashboard.aacsearch.com) - Manage your indexes and settings.
- [API Playground](https://api.aacsearch.com/playground) - Test API calls directly in your browser.
- [Full API Reference](../api/search.md) - Detailed documentation on all endpoints.

This quickstart covers the basics to get you up and running with the AACSearch API. Dive into other sections of the documentation for advanced features and best practices.
