# Typo Tolerance

This guide explains how to configure typo tolerance in AACSearch to ensure users still find relevant results even when their queries contain spelling mistakes or typos.

## Introduction

Typo tolerance allows your search engine to handle misspelled or mistyped queries by matching them to the closest correct terms in your index. AACSearch provides flexible settings to control how forgiving your search is to errors, balancing between accuracy and user convenience to improve the search experience.

## Accessing Typo Tolerance Settings

1. **Navigate to Indexes**: From the sidebar menu in the dashboard, select "Indexes."
2. **Select an Index**: Click on the index you want to configure.
3. **Go to Search Configuration**: In the index details, find the "Search Configuration" tab or section, then look for "Typo Tolerance" or "Spelling Errors" settings.

## Understanding Typo Tolerance

- **Typo Detection**: Identifies common spelling mistakes or keyboard errors (e.g., "smratphone" for "smartphone").
- **Correction Mechanism**: Matches misspelled queries to the most likely correct terms based on edit distance (e.g., number of character changes needed).
- **Impact on Results**: Returns results for the corrected term, often with an indication to the user (e.g., "Did you mean...?").

## Setting Up Typo Tolerance

1. **Enable Typo Tolerance**: In the Typo Tolerance settings, toggle the feature on for your index.
2. **Configure Tolerance Levels**:
   - **Minimum Word Length**: Set the minimum length of words for which typo tolerance applies (e.g., ignore typos in very short words like "a" or "the").
   - **Typo Threshold**: Define how many typos are allowed based on word length (e.g., 1 typo for words of 5-8 characters, 2 typos for longer words).
   - **Disable on Specific Fields**: Optionally disable typo tolerance for certain fields where exact matches are critical (e.g., product codes).
3. **Set Priority Rules**:
   - **Exact Matches First**: Prioritize exact matches over typo-corrected results if both are available.
   - **Typo Penalty**: Apply a ranking penalty to typo-corrected results to rank them below exact matches.
4. **Save Changes**: Apply your settings to update the index with the new typo tolerance configuration.

## Customizing Typo Behavior

- **Custom Dictionary**: Add a custom dictionary of common misspellings or domain-specific terms to improve correction accuracy.
- **Language Support**: Configure typo tolerance to account for language-specific spelling patterns or keyboard layouts (e.g., QWERTY vs. AZERTY errors).
- **User Feedback**: Show users the corrected term (e.g., "Showing results for 'smartphone'") and allow them to revert to the original query if needed.

## Testing Typo Tolerance

- **Search Preview**: Use the dashboard's search preview tool to test misspelled queries and see how results are returned with typo tolerance enabled.
- **Analyze Analytics**: Monitor analytics to identify frequent misspellings or queries with no results that could benefit from typo tolerance adjustments.
- **Iterate**: Refine tolerance settings based on user behavior to balance between catching typos and maintaining result relevance.

## Best Practices

- **Set Appropriate Thresholds**: Avoid overly lenient typo tolerance, as it can return irrelevant results (e.g., correcting "cat" to "car" too easily).
- **Prioritize User Intent**: Ensure typo corrections align with likely user intent by focusing on common errors rather than obscure ones.
- **Inform Users**: Clearly indicate when results are based on a corrected query to maintain transparency and trust.
- **Monitor Performance**: Regularly review analytics to ensure typo tolerance improves search success without introducing noise.

## Advanced Typo Tolerance Usage

- **API-Driven Corrections**: Use the AACSearch API to programmatically suggest corrections or handle typo tolerance for custom search interfaces.
- **Machine Learning**: Leverage machine learning to improve typo detection over time based on user interactions and corrections.
- **Contextual Corrections**: Adjust typo tolerance based on query context or user profile (e.g., stricter for technical terms, more lenient for casual searches).

## Troubleshooting

- **Over-Correction**: If typo tolerance changes queries too aggressively, reduce the typo threshold or disable it for specific fields.
- **Missed Corrections**: If obvious typos aren't caught, ensure the minimum word length and typo thresholds are set appropriately.
- **Performance Issues**: Typo tolerance can slow down searches with very large indexes; optimize by limiting correction scope or caching common queries.
- **Contact Support**: For complex typo tolerance issues, reach out to support via [community.aacsearch.com](https://community.aacsearch.com) or email support@aacsearch.com.

## Next Steps

- Learn about tuning relevance in [Relevance Tuning](../search/relevance.md).
- Explore synonym management in [Synonyms](../search/synonyms.md).
- Dive deeper into autocomplete features with [Autocomplete](../search/autocomplete.md).

## Additional Resources

- [AACSearch Dashboard](https://dashboard.aacsearch.com) - Access your account and manage settings.
- [Community Forum](https://community.aacsearch.com) - Connect with other users and get help.
