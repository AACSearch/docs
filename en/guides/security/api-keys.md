# API Key Management

This guide explains how to manage API keys in AACSearch to secure access to your search resources and control usage.

## Introduction

API keys are essential for authenticating and controlling access to AACSearch's API endpoints. Proper management of API keys ensures that only authorized users or applications can interact with your search indexes, protecting your data and resources from unauthorized access. This guide covers best practices for creating, using, and securing API keys in AACSearch.

## Accessing API Key Settings

1. **Navigate to Account Settings**: From the sidebar menu in the dashboard, select "Account" or "Settings."
2. **Go to API Keys Section**: In the account settings, find the "API Keys" or "Developer" tab to manage your keys.
3. **View or Create Keys**: See existing API keys or create new ones as needed for your applications or team members.

## Understanding API Keys

- **Purpose**: API keys act as unique identifiers for authenticating requests to AACSearch APIs, ensuring that only authorized entities can perform actions like searching, indexing, or modifying settings.
- **Scope and Permissions**: API keys can have specific permissions or restrictions (e.g., read-only, write access) to limit what actions can be performed.
- **Usage Tracking**: API keys help track usage and monitor API calls, which is useful for billing, analytics, and detecting abuse.

## Managing API Keys

1. **Creating API Keys**:

   - **Generate New Key**: In the API Keys section, click "Create New Key" or "Generate API Key."
   - **Set Permissions**: Define the scope of the key (e.g., read-only for search queries, full access for administrative tasks) to follow the principle of least privilege.
   - **Name the Key**: Assign a descriptive name to the key (e.g., "Frontend Search App") to easily identify its purpose or owner.
   - **Save and Copy**: After creation, copy the key immediately as it may not be shown again for security reasons. Store it securely.

2. **Using API Keys**:

   - **Include in Requests**: Add the API key to your API requests, typically in the header (e.g., `X-API-Key: your-api-key`) or as a query parameter, depending on AACSearch's API documentation.
   - **Environment Variables**: Store API keys in environment variables or configuration files in your application, never hardcode them directly into source code.
   - **Secure Transmission**: Ensure API requests are made over HTTPS to encrypt the transmission of your API key and prevent interception.

3. **Rotating and Revoking Keys**:

   - **Regular Rotation**: Periodically rotate API keys (e.g., every 90 days) to minimize the risk of compromised keys being used long-term.
   - **Revoke Compromised Keys**: If a key is suspected to be leaked or compromised, revoke it immediately in the API Keys section of the dashboard.
   - **Generate Replacement**: Create a new key before revoking the old one to ensure uninterrupted service for your applications, then update the key in your systems.

4. **Restricting Key Usage**:
   - **IP Whitelisting**: If supported, restrict API keys to specific IP addresses or ranges to prevent usage from unauthorized locations.
   - **Rate Limiting**: Apply rate limits to API keys to prevent abuse or overuse, protecting your resources from excessive requests.
   - **Scoped Access**: Limit keys to specific indexes or operations (e.g., only allow searching on a particular index) to reduce potential damage if a key is compromised.

## Best Practices for API Key Security

- **Never Share Publicly**: Do not expose API keys in public repositories (e.g., GitHub), client-side code, or unsecured communications like email.
- **Use Secure Storage**: Store API keys in secure vaults or secret management tools (e.g., AWS Secrets Manager, HashiCorp Vault) rather than plain text files.
- **Monitor Usage**: Regularly review API key usage logs in the AACSearch dashboard to detect unusual activity or unauthorized access attempts.
- **Least Privilege Principle**: Grant only the permissions necessary for the key's intended use to minimize the impact of a potential breach.
- **Educate Team Members**: Ensure all team members understand the importance of API key security and follow best practices for handling them.

## Testing API Keys

- **Validate Functionality**: Test newly created API keys with sample API calls to ensure they work as expected with the assigned permissions.
- **Check Restrictions**: Verify that restrictions (e.g., IP whitelisting, scoped access) are enforced by attempting unauthorized actions or accessing from restricted locations.
- **Monitor Logs**: After testing, check usage logs to confirm that the API key activity matches your test actions, ensuring no unexpected behavior.

## Advanced API Key Management

- **Programmatic Key Management**: Use the AACSearch API to programmatically create, rotate, or revoke API keys for automated workflows or integration with your security systems.
- **Key Rotation Schedules**: Implement automated key rotation using scripts or CI/CD pipelines to enforce regular updates without manual intervention.
- **Audit Trails**: Enable detailed logging for API key actions if supported, creating an audit trail for security reviews or compliance requirements.

## Troubleshooting

- **API Key Not Working**: If a key fails authentication, ensure it hasn't been revoked, check for typos when copying the key, and verify that permissions match the intended action.
- **Unauthorized Access Errors**: Confirm the key has the correct scope for the operation and is being used from an allowed IP or context if restrictions are applied.
- **Suspected Compromise**: If you suspect a key leak, revoke it immediately, generate a new key, and review access logs for suspicious activity.
- **Contact Support**: For complex API key issues or suspected security breaches, reach out to support via [community.aacsearch.com](https://community.aacsearch.com) or email support@aacsearch.com.

## Next Steps

- Learn about access control in [Access Control](../security/access-control.md).
- Explore rate limiting strategies in [Rate Limiting](../security/rate-limiting.md).
- Dive deeper into data privacy with [Data Privacy](../security/privacy.md).

## Additional Resources

- [AACSearch Dashboard](https://dashboard.aacsearch.com) - Access your account and manage settings.
- [Community Forum](https://community.aacsearch.com) - Connect with other users and get help.
