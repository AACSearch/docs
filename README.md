# AACSearch Documentation

Полная документация для платформы поиска AACSearch - руководства, API reference, примеры и best practices.

## 📚 Структура документации

```
docs/
├── api/                    # API Reference
├── guides/                 # Руководства пользователя
├── examples/               # Примеры кода
├── sdk/                    # Документация SDK
├── tutorials/              # Пошаговые туториалы
├── advanced/               # Продвинутые темы
├── integrations/           # Интеграции с внешними системами
└── troubleshooting/        # Решение проблем
```

## 🚀 Быстрый старт

### Для новых пользователей
- [Создание аккаунта](./guides/getting-started/account-setup.md)
- [Первый индекс поиска](./guides/getting-started/first-index.md)
- [Загрузка данных](./guides/getting-started/data-upload.md)
- [Интеграция поиска](./guides/getting-started/integration.md)

### Для разработчиков
- [API Quickstart](./api/quickstart.md)
- [SDK Installation](./sdk/installation.md)
- [Authentication](./api/authentication.md)
- [Code Examples](./examples/README.md)

## 📖 Основные разделы

### 🔌 API Reference
- [Search API](./api/search.md) - Выполнение поисковых запросов
- [Index API](./api/index.md) - Управление индексами
- [Objects API](./api/objects.md) - Добавление, обновление, удаление объектов
- [Analytics API](./api/analytics.md) - Получение статистики
- [Settings API](./api/settings.md) - Настройка параметров поиска

### 📋 Руководства пользователя
- [Dashboard Overview](./guides/dashboard/overview.md) - Обзор панели управления
- [Index Management](./guides/dashboard/indexes.md) - Управление индексами
- [Search Configuration](./guides/dashboard/search-config.md) - Настройка поиска
- [Analytics & Insights](./guides/dashboard/analytics.md) - Аналитика и метрики
- [Team Management](./guides/dashboard/teams.md) - Управление командой

### 🛠 SDK Документация
- [JavaScript SDK](./sdk/javascript.md) - Интеграция в веб-приложения
- [React Components](./sdk/react.md) - Готовые React компоненты
- [Vue Components](./sdk/vue.md) - Компоненты для Vue.js
- [Python SDK](./sdk/python.md) - Backend интеграция на Python
- [Mobile SDKs](./sdk/mobile.md) - iOS и Android SDK

### 💡 Примеры и туториалы
- [E-commerce Search](./examples/ecommerce/README.md) - Поиск для интернет-магазинов
- [Content Search](./examples/content/README.md) - Поиск по контенту
- [Multi-tenant Search](./examples/multi-tenant/README.md) - Мультитенантный поиск
- [Geo Search](./examples/geo/README.md) - Геопоиск

## 🎯 Популярные темы

### Настройка поиска
- [Relevance Tuning](./guides/search/relevance.md) - Настройка релевантности
- [Synonyms](./guides/search/synonyms.md) - Работа с синонимами
- [Faceted Search](./guides/search/facets.md) - Фасетный поиск
- [Autocomplete](./guides/search/autocomplete.md) - Автодополнение
- [Typo Tolerance](./guides/search/typos.md) - Толерантность к опечаткам

### Производительность
- [Indexing Best Practices](./guides/performance/indexing.md) - Лучшие практики индексации
- [Query Optimization](./guides/performance/queries.md) - Оптимизация запросов
- [Caching Strategies](./guides/performance/caching.md) - Стратегии кэширования
- [Scaling](./guides/performance/scaling.md) - Масштабирование

### Безопасность
- [API Key Management](./guides/security/api-keys.md) - Управление API ключами
- [Access Control](./guides/security/access-control.md) - Контроль доступа
- [Rate Limiting](./guides/security/rate-limiting.md) - Ограничение запросов
- [Data Privacy](./guides/security/privacy.md) - Конфиденциальность данных

## 🔧 Интеграции

### CMS и платформы
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

## 🧩 Продвинутые темы

### Алгоритмы поиска
- [Ranking Algorithms](./advanced/ranking.md) - Алгоритмы ранжирования
- [Machine Learning](./advanced/ml.md) - Машинное обучение в поиске
- [Natural Language Processing](./advanced/nlp.md) - Обработка естественного языка
- [Vector Search](./advanced/vector-search.md) - Векторный поиск

### Архитектура
- [System Architecture](./advanced/architecture.md) - Архитектура системы
- [Data Flow](./advanced/data-flow.md) - Поток данных
- [Distributed Search](./advanced/distributed.md) - Распределенный поиск
- [High Availability](./advanced/ha.md) - Высокая доступность

### Кастомизация
- [Custom Ranking](./advanced/custom-ranking.md) - Пользовательское ранжирование
- [Plugin Development](./advanced/plugins.md) - Разработка плагинов
- [Custom Analytics](./advanced/custom-analytics.md) - Пользовательская аналитика
- [Webhooks](./advanced/webhooks.md) - Веб-хуки

## 🐛 Устранение неисправностей

### Частые проблемы
- [Common Issues](./troubleshooting/common-issues.md) - Частые проблемы
- [Performance Issues](./troubleshooting/performance.md) - Проблемы производительности
- [API Errors](./troubleshooting/api-errors.md) - Ошибки API
- [SDK Troubleshooting](./troubleshooting/sdk.md) - Проблемы с SDK

### Диагностика
- [Debug Mode](./troubleshooting/debug.md) - Режим отладки
- [Logs Analysis](./troubleshooting/logs.md) - Анализ логов
- [Health Checks](./troubleshooting/health-checks.md) - Проверки состояния

## 📊 API Reference

### Endpoints
```
GET    /search                 # Поиск объектов
POST   /indexes               # Создание индекса
GET    /indexes               # Список индексов
PUT    /indexes/{name}        # Обновление индекса
DELETE /indexes/{name}        # Удаление индекса
POST   /indexes/{name}/objects # Добавление объектов
PUT    /indexes/{name}/objects/{id} # Обновление объекта
DELETE /indexes/{name}/objects/{id} # Удаление объекта
GET    /analytics             # Получение аналитики
```

### Параметры поиска
- `q` - Поисковый запрос
- `filters` - Фильтры
- `facets` - Фасеты для агрегации
- `attributesToRetrieve` - Поля для возврата
- `attributesToHighlight` - Поля для подсветки
- `page` - Номер страницы
- `hitsPerPage` - Количество результатов на странице
- `sortBy` - Сортировка результатов

### Примеры запросов

#### Простой поиск
```bash
curl -X GET "https://api.aacsearch.com/search" \
  -H "X-API-Key: your-api-key" \
  -G \
  -d "q=smartphone" \
  -d "index=products"
```

#### Поиск с фильтрами
```bash
curl -X GET "https://api.aacsearch.com/search" \
  -H "X-API-Key: your-api-key" \
  -G \
  -d "q=smartphone" \
  -d "index=products" \
  -d "filters=category:electronics AND price:100 TO 1000" \
  -d "facets=brand,price"
```

## 🎓 Учебные материалы

### Пошаговые туториалы
- [Building Search UI](./tutorials/search-ui.md) - Создание поискового интерфейса
- [Implementing Autocomplete](./tutorials/autocomplete.md) - Реализация автодополнения
- [Setting up Analytics](./tutorials/analytics.md) - Настройка аналитики
- [Multi-language Search](./tutorials/multi-language.md) - Многоязычный поиск

### Video Guides
- [Getting Started Video Series](./guides/videos/getting-started.md)
- [Advanced Configuration](./guides/videos/advanced-config.md)
- [Performance Optimization](./guides/videos/performance.md)

## 🔗 Полезные ссылки

- [AACSearch Dashboard](https://dashboard.aacsearch.com)
- [API Playground](https://api.aacsearch.com/playground)
- [Community Forum](https://community.aacsearch.com)
- [GitHub Repository](https://github.com/AACSearch)
- [Status Page](https://status.aacsearch.com)

## 🤝 Участие в документации

Мы приветствуем вклад в улучшение документации!

1. Форкните репозиторий
2. Создайте ветку для изменений
3. Внесите улучшения
4. Создайте Pull Request

### Стиль написания
- Используйте простой и понятный язык
- Добавляйте примеры кода
- Структурируйте контент с помощью заголовков
- Проверяйте ссылки на актуальность

## 📝 Changelog

Все значимые изменения в документации фиксируются в [CHANGELOG.md](./CHANGELOG.md).

## 📄 Лицензия

Документация распространяется под лицензией [Creative Commons Attribution 4.0](https://creativecommons.org/licenses/by/4.0/).