# Faceted Search

This guide explains how to set up and manage faceted search in AACSearch to allow users to filter results by specific attributes or categories.

## Introduction

Faceted search, also known as faceted navigation, enables users to refine search results by applying filters based on predefined attributes like category, price, brand, or other metadata. AACSearch provides robust tools to implement faceted search, improving user experience by making it easier to narrow down results to the most relevant items.

## Accessing Facet Settings

1. **Navigate to Indexes**: From the sidebar menu in the dashboard, select "Indexes."
2. **Select an Index**: Click on the index you want to configure.
3. **Go to Search Configuration**: In the index details, find the "Search Configuration" tab or section, then look for "Facets" or "Faceted Search" settings.

## Understanding Facets

- **Facet Definition**: A facet is an attribute or field in your data (e.g., "category," "price range") that users can use to filter search results.
- **Facet Values**: The specific options within a facet (e.g., for the "category" facet, values might be "electronics," "clothing," "books").
- **Facet Filters**: The mechanism by which users select facet values to narrow down search results.

## Setting Up Facets

1. **Define Facets**: In the Facets settings, click "Add Facet" or select fields from your data schema to be used as facets.
2. **Configure Facet Properties**:
   - **Name**: Give the facet a user-friendly name (e.g., "Product Category").
   - **Field**: Map it to the corresponding field in your data.
   - **Type**: Specify if it's a categorical facet (e.g., "brand") or a range facet (e.g., "price").
3. **Set Display Options**:
   - **Order**: Determine the order in which facets appear in the search UI.
   - **Visibility**: Choose whether a facet is always visible or only appears when relevant.
   - **Limit Values**: Set a limit on the number of facet values displayed to avoid overwhelming users.
4. **Save Changes**: Apply your settings to update the index with the new facet configuration.

## Managing Facet Filters

- **Enable Multi-Selection**: Allow users to select multiple values within a single facet (e.g., filter by both "electronics" and "clothing").
- **Combine Facets**: Let users apply filters across multiple facets (e.g., "category: electronics" AND "price: under $100").
- **Filter Logic**: Choose between "AND" (all conditions must match) and "OR" (any condition can match) logic for multi-selected values.

## Customizing Facet Display in UI

- **Facet Widgets**: Use AACSearch SDKs or components to integrate facets into your search interface as dropdowns, checkboxes, sliders (for ranges), or other UI elements.
- **Dynamic Counts**: Display the number of matching results for each facet value (e.g., "electronics (120)"), updating dynamically as filters are applied.
- **Hierarchical Facets**: For nested categories (e.g., "electronics > phones > smartphones"), configure hierarchical facets to guide users through subcategories.

## Testing Faceted Search

- **Search Preview**: Use the dashboard's search preview tool to test how facets filter results with different queries and filter combinations.
- **Analyze Analytics**: Monitor analytics to see which facets users interact with most and whether certain facets lead to higher engagement or conversions.
- **Iterate**: Adjust facet configurations based on user behavior to prioritize the most useful filters.

## Best Practices

- **Choose Relevant Facets**: Select facets that align with how users naturally want to filter content (e.g., price for e-commerce, location for geo-search).
- **Limit Facet Overload**: Avoid displaying too many facets or values at once; focus on the most impactful ones to keep the UI clean.
- **Provide Clear Labels**: Use intuitive names for facets and values so users understand what each filter does.
- **Support Ranges for Numeric Data**: For fields like price or date, use range facets (e.g., sliders or min/max inputs) instead of listing every possible value.

## Advanced Facet Usage

- **Dynamic Facets**: Automatically generate facets based on the most common attributes in search results for a given query.
- **API-Driven Facets**: Use the AACSearch API to programmatically manage facets for custom or real-time filtering needs.
- **Personalized Facets**: Show different facets or prioritize certain values based on user context or preferences (requires advanced setup).

## Troubleshooting

- **Facets Not Appearing**: Ensure the facet fields are correctly mapped to your data schema and that the index is updated.
- **Incorrect Counts**: If facet value counts don't match results, verify that data is fully indexed and there are no discrepancies in field values.
- **Slow Performance**: Too many facets or complex filter combinations can impact speed; optimize by limiting facet values or caching common queries.
- **Contact Support**: For complex facet issues, reach out to support via [community.aacsearch.com](https://community.aacsearch.com) or email support@aacsearch.com.

## Next Steps

- Learn about tuning relevance in [Relevance Tuning](../search/relevance.md).
- Explore synonym management in [Synonyms](../search/synonyms.md).
- Dive deeper into autocomplete features with [Autocomplete](../search/autocomplete.md).

## Additional Resources

- [AACSearch Dashboard](https://dashboard.aacsearch.com) - Access your account and manage settings.
- [Community Forum](https://community.aacsearch.com) - Connect with other users and get help.
