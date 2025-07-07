# Data Privacy

Data privacy is a core priority at AACSearch. We are committed to protecting the information you entrust to us, whether it's your personal data or the data you index for search. This guide outlines how AACSearch handles data privacy, the measures we take to secure your information, and the tools and practices you can use to ensure compliance with privacy regulations.

## Our Commitment to Privacy

AACSearch adheres to strict privacy standards to safeguard your data and comply with global regulations such as the General Data Protection Regulation (GDPR), the California Consumer Privacy Act (CCPA), and other applicable laws. Our privacy practices are designed to:

- **Protect User Data**: Ensure that personal and indexed data is handled securely and only used for the purposes you authorize.
- **Provide Transparency**: Clearly communicate how data is collected, stored, processed, and protected.
- **Empower Control**: Offer tools and settings for you to manage data access, retention, and deletion.
- **Maintain Compliance**: Align with international privacy laws to support your compliance efforts.

For a detailed overview of our policies, refer to the [AACSearch Privacy Policy](https://aacsearch.com/privacy-policy).

## Data We Collect and Process

AACSearch handles two primary categories of data:

1. **Account and Usage Data**:

   - **Personal Information**: Data provided during account creation, such as name, email address, and billing information.
   - **Usage Data**: Information about how you interact with AACSearch, including API usage statistics, dashboard activity, and support interactions.
   - **Purpose**: This data is used to manage your account, provide customer support, improve our services, and comply with legal obligations.

2. **Indexed Data**:
   - **Search Content**: Data you upload to your indexes for search functionality, which may include customer records, product information, or other content.
   - **Purpose**: This data is processed solely to enable search capabilities within your application. AACSearch does not use indexed data for any purpose beyond what is necessary to provide the service.

## How We Protect Your Data

AACSearch implements robust security measures to protect both account and indexed data:

- **Encryption**:
  - All data transmitted between your application and AACSearch is encrypted using TLS (Transport Layer Security) to prevent interception.
  - Data at rest, including indexed content and backups, is encrypted using industry-standard algorithms (e.g., AES-256).
- **Access Controls**:
  - Access to your data is restricted to authorized personnel only, with strict role-based access controls (RBAC).
  - API keys are used to authenticate requests, and you can set granular permissions to limit access. See [API Key Management](../security/api-keys.md) for details.
- **Secure Infrastructure**:
  - Our servers are hosted in secure, compliant data centers with physical and environmental protections.
  - Regular security audits and vulnerability assessments are conducted to identify and mitigate risks.
- **Data Isolation**:
  - Each customer's data is logically separated to prevent unauthorized access between accounts.
  - Indexed data is isolated per index, ensuring that searches are scoped to your specific data set.
- **Monitoring and Incident Response**:
  - We continuously monitor for suspicious activity and maintain an incident response plan to address potential breaches swiftly.
  - In the event of a security incident, affected customers are notified promptly in accordance with legal requirements.

## Your Responsibilities for Data Privacy

While AACSearch provides the infrastructure and tools to secure your data, you also have responsibilities to ensure privacy, especially when handling personal information in your indexed data:

- **Data Minimization**: Only upload data to AACSearch that is necessary for search functionality. Avoid including sensitive personal information (e.g., Social Security numbers, health records) unless absolutely required and properly secured.
- **User Consent**: If your indexed data includes personal information, ensure you have obtained appropriate consent from users to process and store their data in accordance with applicable laws like GDPR or CCPA.
- **Access Control**: Use AACSearch's access control features to limit who can view or manage data within your indexes. Configure API key permissions to restrict access to sensitive operations. See [Access Control](../security/access-control.md).
- **Data Retention**: Regularly review and delete outdated or unnecessary data from your indexes to minimize exposure. Use the [Objects API](../../api/objects.md) to remove obsolete records.
- **Compliance**: Ensure your use of AACSearch aligns with privacy regulations relevant to your region and industry. Consult legal counsel if needed to understand your obligations.

## Privacy Features in AACSearch

AACSearch offers several features to help you manage data privacy effectively:

- **Data Deletion**:
  - You can delete individual objects or entire indexes at any time using the [Objects API](../../api/objects.md) or the dashboard.
  - Account deletion requests can be initiated through support, which will remove all associated data in compliance with privacy laws.
- **Data Export**:
  - Export your indexed data or account information via the dashboard or API to fulfill data portability requests under GDPR or CCPA.
- **API Key Permissions**:
  - Configure API keys with specific permissions (e.g., read-only, write-only) to limit access to sensitive data or operations. See [API Key Management](../security/api-keys.md).
- **Audit Logs**:
  - Enterprise plans include access to audit logs to track API activity and monitor for unauthorized access. Contact support for details on enabling this feature.
- **Data Processing Agreements (DPA)**:
  - For customers subject to GDPR or other regulations, AACSearch provides a Data Processing Agreement to formalize our role as a data processor. Request a DPA through [support@aacsearch.com](mailto:support@aacsearch.com).

## Handling Personal Data in Indexed Content

If your application indexes personal data (e.g., customer names, emails), take extra precautions to ensure privacy:

1. **Anonymize Data**: Where possible, anonymize or pseudonymize personal data before uploading it to AACSearch to reduce risk. For example, replace identifiable fields with unique identifiers.
2. **Secure API Keys**: Treat API keys as sensitive credentials. Avoid exposing them in client-side code or public repositories. Use environment variables or secure key management systems. See [API Key Management](../security/api-keys.md).
3. **Limit Searchable Attributes**: Configure index settings to exclude sensitive fields from search results if they are not needed. See [Settings API](../../api/settings.md) for configuration options.
4. **Implement Access Controls**: Use filters or restricted API keys to ensure that search results are only accessible to authorized users. See [Access Control](../security/access-control.md).
5. **Monitor Usage**: Regularly review analytics to detect unusual access patterns that might indicate a privacy breach. See [Analytics API](../../api/analytics.md).

## Compliance with Privacy Regulations

AACSearch is designed to support your compliance with major privacy regulations:

- **GDPR (General Data Protection Regulation)**:
  - AACSearch acts as a data processor for indexed content and provides tools for data deletion, export, and access control to help you meet GDPR requirements.
  - We maintain data residency options for EU customers to ensure data is stored within the European Economic Area (EEA). Contact support for configuration details.
- **CCPA (California Consumer Privacy Act)**:
  - Tools for data export and deletion support CCPA requirements for consumer data access and opt-out requests.
- **Other Regulations**: AACSearch's privacy features can be adapted to comply with other regional laws, such as PIPEDA (Canada) or LGPD (Brazil). Consult with legal counsel to ensure full compliance.

To request documentation or certifications demonstrating AACSearch's compliance (e.g., SOC 2 reports), contact [support@aacsearch.com](mailto:support@aacsearch.com).

## Data Retention and Deletion

- **Account Data Retention**: Personal information associated with your account is retained as long as your account is active. Upon account deletion, data is removed within 30 days, except where longer retention is required by law (e.g., billing records for tax purposes).
- **Indexed Data Retention**: Indexed data remains in your indexes until you delete it manually or terminate your account. You can configure automated data expiration policies for specific indexes on enterprise plans; contact support for setup.
- **Backups**: Data backups are retained for disaster recovery purposes for a limited period (typically 14-30 days) before being securely deleted. Backup data is encrypted and access-controlled.

## Reporting Privacy Concerns

If you have concerns about data privacy or suspect a breach:

- **Contact Support**: Reach out to [support@aacsearch.com](mailto:support@aacsearch.com) or through the [Community Forum](https://community.aacsearch.com) for immediate assistance.
- **Data Protection Officer (DPO)**: For GDPR-related inquiries, contact our DPO at [dpo@aacsearch.com](mailto:dpo@aacsearch.com).
- **Incident Reporting**: If you believe personal data has been compromised, report it immediately so we can investigate and take appropriate action.

## Troubleshooting Privacy Issues

If you encounter issues related to data privacy:

- **Data Not Deleting**: If objects or account data are not deleting as expected, verify your API key permissions and ensure no active subscriptions or dependencies prevent deletion. Contact support if issues persist.
- **Unauthorized Access**: If you suspect unauthorized access to your data, revoke affected API keys immediately in the dashboard and generate new ones. Enable audit logs (if available) to investigate. See [API Key Management](../security/api-keys.md).
- **Compliance Questions**: For help with GDPR, CCPA, or other compliance requirements, reach out to support for documentation or guidance on using privacy features.
- **Data Export Failures**: If data export fails, ensure your account has sufficient permissions and storage space. Retry using the API if dashboard export fails. See [Objects API](../../api/objects.md) for export methods.

## Additional Resources

- [AACSearch Privacy Policy](https://aacsearch.com/privacy-policy) - Full details on our data handling practices.
- [AACSearch Dashboard](https://dashboard.aacsearch.com) - Manage data, API keys, and account settings.
- [API Key Management](../security/api-keys.md) - Secure your API keys to protect data access.
- [Access Control](../security/access-control.md) - Configure permissions to limit data exposure.
- [Objects API](../../api/objects.md) - Manage data deletion and export programmatically.
- [Community Forum](https://community.aacsearch.com) - Connect with other users for privacy best practices and support.
