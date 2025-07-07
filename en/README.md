# AACSearch Documentation

Complete documentation for the AACSearch search platform - guides, API reference, examples, and best practices.

## 📚 Documentation Structure

```
docs/en/
├── api/                    # API Reference
├── guides/                 # User Guides
├── examples/               # Code Examples
├── sdk/                    # SDK Documentation
├── tutorials/              # Step-by-Step Tutorials
├── advanced/               # Advanced Topics
├── integrations/           # Integrations with External Systems
└── troubleshooting/        # Problem Resolution
```

## 🚀 Quick Start

### For New Users

- [Account Setup](./guides/getting-started/account-setup.md)
- [First Search Index](./guides/getting-started/first-index.md)
- [Data Upload](./guides/getting-started/data-upload.md)
- [Search Integration](./guides/getting-started/integration.md)

### For Developers

- [API Quickstart](./api/quickstart.md)
- [SDK Installation](./sdk/installation.md)
- [Authentication](./api/authentication.md)
- [Code Examples](./examples/README.md)

## 📖 Main Sections

### 🔌 API Reference

- [Search API](./api/search.md) - Performing search queries
- [Index API](./api/index.md) - Managing indexes
- [Objects API](./api/objects.md) - Adding, updating, deleting objects
- [Analytics API](./api/analytics.md) - Retrieving statistics
- [Settings API](./api/settings.md) - Configuring search parameters

### 📋 User Guides

- [Dashboard Overview](./guides/dashboard/overview.md) - Overview of the control panel
- [Index Management](./guides/dashboard/indexes.md) - Managing indexes
- [Search Configuration](./guides/dashboard/search-config.md) - Customizing search
- [Analytics & Insights](./guides/dashboard/analytics.md) - Analytics and metrics
- [Team Management](./guides/dashboard/teams.md) - Managing team access

### 🛠 SDK Documentation

- [JavaScript SDK](./sdk/javascript.md) - Integration in web applications
- [React Components](./sdk/react.md) - Ready-to-use React components
- [Vue Components](./sdk/vue.md) - Components for Vue.js
- [Python SDK](./sdk/python.md) - Backend integration with Python
- [Mobile SDKs](./sdk/mobile.md) - iOS and Android SDKs

### 💡 Examples and Tutorials

- [E-commerce Search](./examples/ecommerce/README.md) - Search for online stores
- [Content Search](./examples/content/README.md) - Content search
- [Multi-tenant Search](./examples/multi-tenant/README.md) - Multi-tenant search
- [Geo Search](./examples/geo/README.md) - Geospatial search

## 🎯 Popular Topics

### Search Customization

- [Relevance Tuning](./guides/search/relevance.md) - Adjusting relevance
- [Synonyms](./guides/search/synonyms.md) - Working with synonyms
- [Faceted Search](./guides/search/facets.md) - Faceted search
- [Autocomplete](./guides/search/autocomplete.md) - Autocompletion
- [Typo Tolerance](./guides/search/typos.md) - Tolerance to typos

### Performance

- [Indexing Best Practices](./guides/performance/indexing.md) - Best practices for indexing
- [Query Optimization](./guides/performance/queries.md) - Optimizing queries
- [Caching Strategies](./guides/performance/caching.md) - Caching strategies
- [Scaling](./guides/performance/scaling.md) - Scaling search

### Security

- [API Key Management](./guides/security/api-keys.md) - Managing API keys
- [Access Control](./guides/security/access-control.md) - Access control
- [Rate Limiting](./guides/security/rate-limiting.md) - Request limiting
- [Data Privacy](./guides/security/privacy.md) - Data privacy

## 🔧 Integrations

### CMS and Platforms

- [WordPress Plugin](./integrations/wordpress.md)
- [Shopify App](./integrations/shopify.md)
- [Magento Extension](./integrations/magento.md)
- [Drupal Module](./integrations/drupal.md)

### Frameworks

- [Next.js Integration](./integrations/nextjs.md)
- [Nuxt.js Integration](./integrations/nuxtjs.md)
- [Gatsby Plugin](./integrations/gatsby.md)
- [SvelteKit Integration](./integrations/sveltekit.md)

### Analytics

- [Google Analytics](./integrations/google-analytics.md)
- [Mixpanel Integration](./integrations/mixpanel.md)
- [Segment Integration](./integrations/segment.md)

## 🧩 Advanced Topics

### Search Algorithms

- [Ranking Algorithms](./advanced/ranking.md) - Ranking algorithms
- [Machine Learning](./advanced/ml.md) - Machine learning in search
- [Natural Language Processing](./advanced/nlp.md) - Natural language processing
- [Vector Search](./advanced/vector-search.md) - Vector search

### Architecture

- [System Architecture](./advanced/architecture.md) - System architecture
- [Data Flow](./advanced/data-flow.md) - Data flow
- [Distributed Search](./advanced/distributed.md) - Distributed search
- [High Availability](./advanced/ha.md) - High availability

### Customization

- [Custom Ranking](./advanced/custom-ranking.md) - Custom ranking
- [Plugin Development](./advanced/plugins.md) - Plugin development
- [Custom Analytics](./advanced/custom-analytics.md) - Custom analytics
- [Webhooks](./advanced/webhooks.md) - Webhooks

## 🐛 Troubleshooting

### Common Issues

- [Common Issues](./troubleshooting/common-issues.md) - Frequent problems
- [Performance Issues](./troubleshooting/performance.md) - Performance problems
- [API Errors](./troubleshooting/api-errors.md) - API errors
- [SDK Troubleshooting](./troubleshooting/sdk.md) - SDK issues

### Diagnostics

- [Debug Mode](./troubleshooting/debug.md) - Debug mode
- [Logs Analysis](./troubleshooting/logs.md) - Log analysis
- [Health Checks](./troubleshooting/health-checks.md) - Health checks

## 📊 API Reference

### Endpoints

```
GET    /search                 # Search for objects
POST   /indexes               # Create an index
GET    /indexes               # List indexes
PUT    /indexes/{name}        # Update an index
DELETE /indexes/{name}        # Delete an index
POST   /indexes/{name}/objects # Add objects
PUT    /indexes/{name}/objects/{id} # Update an object
DELETE /indexes/{name}/objects/{id} # Delete an object
GET    /analytics             # Retrieve analytics
```

### Search Parameters

- `q` - Search query
- `filters` - Filters
- `facets` - Facets for aggregation
- `attributesToRetrieve` - Fields to return
- `attributesToHighlight` - Fields to highlight
- `page` - Page number
- `hitsPerPage` - Results per page
- `sortBy` - Sort results

### Request Examples

#### Simple Search

```bash
curl -X GET "https://api.aacsearch.com/search" \
  -H "X-API-Key: your-api-key" \
  -G \
  -d "q=smartphone" \
  -d "index=products"
```

#### Search with Filters

```bash
curl -X GET "https://api.aacsearch.com/search" \
  -H "X-API-Key: your-api-key" \
  -G \
  -d "q=smartphone" \
  -d "index=products" \
  -d "filters=category:electronics AND price:100 TO 1000" \
  -d "facets=brand,price"
```

## 🎓 Learning Resources

### Step-by-Step Tutorials

- [Building Search UI](./tutorials/search-ui.md) - Building a search interface
- [Implementing Autocomplete](./tutorials/autocomplete.md) - Implementing autocompletion
- [Setting up Analytics](./tutorials/analytics.md) - Setting up analytics
- [Multi-language Search](./tutorials/multi-language.md) - Multi-language search

### Video Guides

- [Getting Started Video Series](./guides/videos/getting-started.md)
- [Advanced Configuration](./guides/videos/advanced-config.md)
- [Performance Optimization](./guides/videos/performance.md)

## 🔗 Useful Links

- [AACSearch Dashboard](https://dashboard.aacsearch.com)
- [API Playground](https://api.aacsearch.com/playground)
- [Community Forum](https://community.aacsearch.com)
- [GitHub Repository](https://github.com/AACSearch)
- [Status Page](https://status.aacsearch.com)

## 🤝 Contributing to Documentation

We welcome contributions to improve the documentation!

1. Fork the repository
2. Create a branch for your changes
3. Make your improvements
4. Submit a Pull Request

### Writing Style

- Use simple and clear language
- Include code examples
- Structure content with headings
- Verify links for accuracy

## 📝 Changelog

All significant changes to the documentation are recorded in [CHANGELOG.md](./CHANGELOG.md).

## 📄 License

This documentation is licensed under [Creative Commons Attribution 4.0](https://creativecommons.org/licenses/by/4.0/).
