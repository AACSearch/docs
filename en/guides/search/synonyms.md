# Synonyms

This guide explains how to manage synonyms in AACSearch to improve search accuracy by accounting for similar or equivalent terms.

## Introduction

Synonyms allow your search engine to understand that different words or phrases can have the same meaning, ensuring users find relevant results even if they use varied terminology. AACSearch supports flexible synonym management to enhance the search experience by mapping related terms together.

## Accessing Synonym Settings

1. **Navigate to Indexes**: From the sidebar menu in the dashboard, select "Indexes."
2. **Select an Index**: Click on the index you want to configure.
3. **Go to Search Configuration**: In the index details, find the "Search Configuration" tab or section, then look for "Synonyms" settings.

## Understanding Synonym Types

- **One-Way Synonyms**: A term maps to another term, but not vice versa. For example, "sneaker" can map to "shoe," so a search for "sneaker" returns results for "shoe," but a search for "shoe" does not return results for "sneaker" specifically.
- **Multi-Way Synonyms (Equivalents)**: All terms in a group are interchangeable. For example, "shoe," "footwear," and "boots" can be set as equivalents, so a search for any of these terms returns results for all of them.
- **Placeholder Synonyms**: Used for dynamic or context-specific mappings, often with API integrations for advanced use cases.

## Adding Synonyms

1. **Create a Synonym**: In the Synonyms settings, click "Add Synonym" or "New Synonym."
2. **Choose Synonym Type**: Select whether it's a one-way or multi-way synonym.
3. **Enter Terms**: Input the primary term and the term(s) it should map to. For multi-way synonyms, list all equivalent terms.
4. **Save Changes**: Apply your settings to update the index with the new synonym mapping.

## Managing Synonyms

- **Edit Synonyms**: Modify existing synonym mappings if user behavior or terminology changes over time.
- **Delete Synonyms**: Remove outdated or incorrect synonym mappings to prevent irrelevant search results.
- **Bulk Import/Export**: For large datasets, use CSV import/export features to manage synonyms efficiently.

## Testing Synonym Impact

- **Search Preview**: Use the dashboard's search preview tool to test queries with and without synonyms to see how results change.
- **Analyze Analytics**: Monitor search analytics to identify queries where synonyms could improve relevance or where existing synonyms cause unexpected results.
- **Iterate**: Refine synonym mappings based on user feedback and search performance data.

## Best Practices

- **Understand User Language**: Research the terms your users commonly use to ensure synonym mappings reflect real-world usage.
- **Avoid Over-Mapping**: Too many synonyms can dilute relevance; focus on high-impact terms that users frequently interchange.
- **Use One-Way for Specificity**: Use one-way synonyms when a broader term shouldn't return results for a narrower term (e.g., "phone" shouldn't always return results for "iPhone").
- **Regularly Update**: Keep synonym lists current as language, products, or user behavior evolve.

## Advanced Synonym Usage

- **API Integration**: Use the AACSearch API to programmatically manage synonyms for dynamic or large-scale applications.
- **Contextual Synonyms**: Define synonyms that apply only in specific contexts or for certain user segments (requires advanced setup).
- **Multi-Language Support**: Manage synonyms for different languages if your search supports multilingual content.

## Troubleshooting

- **Unexpected Results**: If synonyms lead to irrelevant results, check for overly broad mappings or conflicts between one-way and multi-way synonyms.
- **Missing Matches**: Ensure all relevant terms are included in synonym groups and that the index is updated after changes.
- **Performance Issues**: Large synonym lists can impact search speed; optimize by prioritizing critical mappings.
- **Contact Support**: For complex synonym issues, reach out to support via [community.aacsearch.com](https://community.aacsearch.com) or email support@aacsearch.com.

## Next Steps

- Learn about tuning relevance in [Relevance Tuning](../search/relevance.md).
- Explore faceted search in [Faceted Search](../search/facets.md).
- Dive deeper into autocomplete features with [Autocomplete](../search/autocomplete.md).

## Additional Resources

- [AACSearch Dashboard](https://dashboard.aacsearch.com) - Access your account and manage settings.
- [Community Forum](https://community.aacsearch.com) - Connect with other users and get help.
