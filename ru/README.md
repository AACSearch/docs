# Документация AACSearch

Полная документация для платформы поиска AACSearch - руководства, справочник API, примеры и лучшие практики.

## 📚 Структура документации

```
docs/ru/
├── api/                    # Справочник API
├── guides/                 # Руководства пользователя
├── examples/               # Примеры кода
├── sdk/                    # Документация SDK
├── tutorials/              # Пошаговые туториалы
├── advanced/               # Продвинутые темы
├── integrations/           # Интеграции с внешними системами
└── troubleshooting/        # Устранение неисправностей
```

## 🚀 Быстрый старт

### Для новых пользователей

- [Создание аккаунта](./guides/getting-started/account-setup.md)
- [Первый индекс поиска](./guides/getting-started/first-index.md)
- [Загрузка данных](./guides/getting-started/data-upload.md)
- [Интеграция поиска](./guides/getting-started/integration.md)

### Для разработчиков

- [Быстрый старт API](./api/quickstart.md)
- [Установка SDK](./sdk/installation.md)
- [Аутентификация](./api/authentication.md)
- [Примеры кода](./examples/README.md)

## 📖 Основные разделы

### 🔌 Справочник API

- [Search API](./api/search.md) - Выполнение поисковых запросов
- [Index API](./api/index.md) - Управление индексами
- [Objects API](./api/objects.md) - Добавление, обновление, удаление объектов
- [Analytics API](./api/analytics.md) - Получение статистики
- [Settings API](./api/settings.md) - Настройка параметров поиска

### 📋 Руководства пользователя

- [Обзор дашборда](./guides/dashboard/overview.md) - Обзор панели управления
- [Управление индексами](./guides/dashboard/indexes.md) - Управление индексами
- [Настройка поиска](./guides/dashboard/search-config.md) - Настройка поиска
- [Аналитика и метрики](./guides/dashboard/analytics.md) - Аналитика и метрики
- [Управление командой](./guides/dashboard/teams.md) - Управление доступом команды

### 🛠 Документация SDK

- [JavaScript SDK](./sdk/javascript.md) - Интеграция в веб-приложения
- [React Components](./sdk/react.md) - Готовые компоненты для React
- [Vue Components](./sdk/vue.md) - Компоненты для Vue.js
- [Python SDK](./sdk/python.md) - Интеграция на бэкенде с Python
- [Mobile SDKs](./sdk/mobile.md) - SDK для iOS и Android

### 💡 Примеры и туториалы

- [Поиск для e-commerce](./examples/ecommerce/README.md) - Поиск для интернет-магазинов
- [Поиск контента](./examples/content/README.md) - Поиск по контенту
- [Мультитенантный поиск](./examples/multi-tenant/README.md) - Мультитенантный поиск
- [Геопоиск](./examples/geo/README.md) - Геопространственный поиск

## 🎯 Популярные темы

### Настройка поиска

- [Настройка релевантности](./guides/search/relevance.md) - Настройка релевантности
- [Синонимы](./guides/search/synonyms.md) - Работа с синонимами
- [Фасетный поиск](./guides/search/facets.md) - Фасетный поиск
- [Автодополнение](./guides/search/autocomplete.md) - Автодополнение
- [Толерантность к опечаткам](./guides/search/typos.md) - Толерантность к опечаткам

### Производительность

- [Лучшие практики индексации](./guides/performance/indexing.md) - Лучшие практики индексации
- [Оптимизация запросов](./guides/performance/queries.md) - Оптимизация запросов
- [Стратегии кэширования](./guides/performance/caching.md) - Стратегии кэширования
- [Масштабирование](./guides/performance/scaling.md) - Масштабирование поиска

### Безопасность

- [Управление API-ключами](./guides/security/api-keys.md) - Управление API-ключами
- [Контроль доступа](./guides/security/access-control.md) - Контроль доступа
- [Ограничение запросов](./guides/security/rate-limiting.md) - Ограничение запросов
- [Конфиденциальность данных](./guides/security/privacy.md) - Конфиденциальность данных

## 🔧 Интеграции

### CMS и платформы

- [Плагин для WordPress](./integrations/wordpress.md)
- [Приложение для Shopify](./integrations/shopify.md)
- [Расширение для Magento](./integrations/magento.md)
- [Модуль для Drupal](./integrations/drupal.md)

### Фреймворки

- [Интеграция с Next.js](./integrations/nextjs.md)
- [Интеграция с Nuxt.js](./integrations/nuxtjs.md)
- [Плагин для Gatsby](./integrations/gatsby.md)
- [Интеграция с SvelteKit](./integrations/sveltekit.md)

### Аналитика

- [Google Analytics](./integrations/google-analytics.md)
- [Интеграция с Mixpanel](./integrations/mixpanel.md)
- [Интеграция с Segment](./integrations/segment.md)

## 🧩 Продвинутые темы

### Алгоритмы поиска

- [Алгоритмы ранжирования](./advanced/ranking.md) - Алгоритмы ранжирования
- [Машинное обучение](./advanced/ml.md) - Машинное обучение в поиске
- [Обработка естественного языка](./advanced/nlp.md) - Обработка естественного языка
- [Векторный поиск](./advanced/vector-search.md) - Векторный поиск

### Архитектура

- [Архитектура системы](./advanced/architecture.md) - Архитектура системы
- [Поток данных](./advanced/data-flow.md) - Поток данных
- [Распределенный поиск](./advanced/distributed.md) - Распределенный поиск
- [Высокая доступность](./advanced/ha.md) - Высокая доступность

### Кастомизация

- [Пользовательское ранжирование](./advanced/custom-ranking.md) - Пользовательское ранжирование
- [Разработка плагинов](./advanced/plugins.md) - Разработка плагинов
- [Пользовательская аналитика](./advanced/custom-analytics.md) - Пользовательская аналитика
- [Веб-хуки](./advanced/webhooks.md) - Веб-хуки

## 🐛 Устранение неисправностей

### Частые проблемы

- [Частые проблемы](./troubleshooting/common-issues.md) - Частые проблемы
- [Проблемы производительности](./troubleshooting/performance.md) - Проблемы производительности
- [Ошибки API](./troubleshooting/api-errors.md) - Ошибки API
- [Проблемы с SDK](./troubleshooting/sdk.md) - Проблемы с SDK

### Диагностика

- [Режим отладки](./troubleshooting/debug.md) - Режим отладки
- [Анализ логов](./troubleshooting/logs.md) - Анализ логов
- [Проверки состояния](./troubleshooting/health-checks.md) - Проверки состояния

## 📊 Справочник API

### Конечные точки

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
- `hitsPerPage` - Результатов на странице
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

- [Создание поискового интерфейса](./tutorials/search-ui.md) - Создание поискового интерфейса
- [Реализация автодополнения](./tutorials/autocomplete.md) - Реализация автодополнения
- [Настройка аналитики](./tutorials/analytics.md) - Настройка аналитики
- [Многоязычный поиск](./tutorials/multi-language.md) - Многоязычный поиск

### Видео-руководства

- [Серия видео по началу работы](./guides/videos/getting-started.md)
- [Продвинутая настройка](./guides/videos/advanced-config.md)
- [Оптимизация производительности](./guides/videos/performance.md)

## 🔗 Полезные ссылки

- [Дашборд AACSearch](https://dashboard.aacsearch.com)
- [Площадка API](https://api.aacsearch.com/playground)
- [Форум сообщества](https://community.aacsearch.com)
- [Репозиторий GitHub](https://github.com/AACSearch)
- [Страница статуса](https://status.aacsearch.com)

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

## 📝 Журнал изменений

Все значимые изменения в документации фиксируются в [CHANGELOG.md](./CHANGELOG.md).

## 📄 Лицензия

Эта документация распространяется под лицензией [Creative Commons Attribution 4.0](https://creativecommons.org/licenses/by/4.0/).
