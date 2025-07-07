# First Index

Creating your first search index is a crucial step to start using AACSearch for organizing and searching your data. An index is a container for your searchable content, allowing you to store and retrieve data efficiently. This guide will walk you through the process of setting up your first index using the AACSearch Dashboard.

## Prerequisites

Before creating an index, ensure you have completed the following:

- **Account Setup**: You have an active AACSearch account. If not, follow the [Account Setup](../getting-started/account-setup.md) guide.
- **Access to Dashboard**: Log in to the [AACSearch Dashboard](https://dashboard.aacsearch.com) with your credentials.

## Step 1: Navigate to Indexes

Once logged in to the AACSearch Dashboard:

1. **Locate the Indexes Section**: On the left-hand sidebar, click on "Indexes." This section is where you manage all your search indexes.
2. **View Indexes List**: If this is your first time, the list will be empty. You'll see a prompt to create your first index.

## Step 2: Create a New Index

To create your first index:

1. **Click on Create Index**: At the top right of the Indexes page, click the "Create Index" button.
2. **Name Your Index**: In the dialog that appears, enter a unique name for your index. Use a descriptive name that reflects the data it will contain (e.g., "products" for an e-commerce catalog or "articles" for a blog).
   - **Note**: Index names must be lowercase, alphanumeric, and can include hyphens (e.g., "my-products-index"). Spaces and special characters are not allowed.
3. **Set Primary Language (Optional)**: Choose the primary language for the content in this index. This helps AACSearch optimize search for language-specific features like stemming and stop words. You can change this later.
4. **Confirm Creation**: Click "Create" to finalize the setup. Your new index will appear in the list.

## Step 3: Configure Basic Settings

After creating the index, you can configure its basic settings to tailor search behavior:

1. **Select Your Index**: Click on the newly created index from the list to open its configuration page.
2. **Define Searchable Attributes**: Under the "Schema" or "Settings" tab, specify which fields in your data should be searchable. For example, if your data includes "title" and "description," add these as searchable attributes.
   - **Tip**: Prioritize important fields (like "title") by listing them first, as this can influence ranking.
3. **Set Filterable Attributes (Optional)**: Define fields that can be used for filtering results (e.g., "category" or "price"). This is useful for narrowing down search results.
4. **Save Changes**: Click "Save Settings" to apply your configuration. These settings can be adjusted later as needed.

## Step 4: Verify Index Creation

To confirm your index is ready:

1. **Check Status**: Return to the Indexes list in the dashboard. Your index should show a status of "Active" or "Ready."
2. **View Details**: Click on the index to see its details, including the number of objects (currently 0 since no data has been added) and configuration summary.

## Next Steps

With your first index created, you're ready to populate it with data and integrate search functionality into your application:

- **[Data Upload](../getting-started/data-upload.md)**: Learn how to add data to your index for searching.
- **[Integration](../getting-started/integration.md)**: Integrate AACSearch into your application or website to enable search.
- **[Search Configuration](../dashboard/search-config.md)**: Explore advanced settings to fine-tune search relevance and performance.

## Troubleshooting

If you encounter issues while creating your first index:

- **Naming Errors**: Ensure the index name follows the required format (lowercase, alphanumeric, hyphens only). If the name is already in use, choose a different one.
- **Permission Issues**: Verify that your account or API key has the necessary permissions to create indexes. If not, contact your organization admin or support.
- **Dashboard Not Responding**: If the dashboard is slow or unresponsive, refresh the page or check your internet connection. If the issue persists, report it to support@aacsearch.com.
- **Contact Support**: For further assistance, reach out to our support team via [community.aacsearch.com](https://community.aacsearch.com) or email support@aacsearch.com.

## Additional Resources

- [AACSearch Dashboard](https://dashboard.aacsearch.com) - Manage your indexes and settings.
- [Index Management](../dashboard/indexes.md) - Learn more about managing indexes via the dashboard.
- [API Reference for Indexes](../../api/index.md) - Use the API to create and manage indexes programmatically.
- [Community Forum](https://community.aacsearch.com) - Connect with other users for tips and troubleshooting.
