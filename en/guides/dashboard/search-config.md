# Search Configuration

This guide covers how to customize search settings in the AACSearch Dashboard to optimize the search experience for your users.

## Introduction

AACSearch allows you to fine-tune search behavior to match the specific needs of your application or website. Through the dashboard, you can adjust relevance, define synonyms, set up faceted search, and more to ensure users find the most relevant results quickly.

## Accessing Search Configuration

1. **Navigate to Indexes**: From the sidebar menu in the dashboard, select "Indexes."
2. **Select an Index**: Click on the index for which you want to configure search settings.
3. **Go to Search Configuration**: In the index details, find the "Search Configuration" tab or section.

## Configuring Relevance

- **Ranking Rules**: Define how results are ranked based on attributes like popularity, date, or custom metrics.
- **Searchable Attributes**: Specify which fields in your data should be searched when a user enters a query.
- **Custom Ranking**: Add custom ranking criteria to prioritize certain results over others.

## Setting Up Synonyms

- **Add Synonyms**: Group similar terms together (e.g., "shoe" and "footwear") to ensure users find results regardless of the exact term used.
- **One-Way Synonyms**: Define synonyms that apply in one direction (e.g., "sneaker" maps to "shoe," but not vice versa).
- **Multi-Way Synonyms**: Create synonym groups where all terms are interchangeable.

## Enabling Faceted Search

- **Define Facets**: Select attributes (e.g., category, price, brand) that users can use to filter search results.
- **Facet Display**: Configure how facets appear in your search UI, including order and visibility.
- **Facet Filters**: Allow users to combine multiple facet filters for precise results.

## Autocomplete and Query Suggestions

- **Enable Autocomplete**: Turn on autocomplete to suggest search terms as users type.
- **Query Suggestions**: Provide popular or trending search terms to guide users to relevant content.

## Typo Tolerance

- **Enable Typo Tolerance**: Allow search results to appear even if the user's query contains typos or misspellings.
- **Configure Tolerance Levels**: Adjust how many typos are tolerated based on word length or query complexity.

## Advanced Settings

- **Highlighting**: Choose which fields to highlight in search results to show users where their query matched.
- **Pagination**: Set the number of results per page and configure pagination behavior.
- **Sorting Options**: Allow users to sort results by different criteria (e.g., price low to high, newest first).

## Testing Your Configuration

- **Search Preview**: Use the dashboard's search preview tool to test how results appear with your current settings.
- **Adjust as Needed**: Based on preview results, tweak settings to improve relevance or user experience.

## Next Steps

- Learn how to manage indexes in [Index Management](../dashboard/indexes.md).
- Analyze search performance in [Analytics & Insights](../dashboard/analytics.md).
- Explore advanced search customization in [Relevance Tuning](../../guides/search/relevance.md).

## Additional Resources

- [AACSearch Dashboard](https://dashboard.aacsearch.com) - Access your account and manage settings.
- [Community Forum](https://community.aacsearch.com) - Connect with other users and get help.
