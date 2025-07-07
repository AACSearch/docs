# API настроек

API настроек позволяет конфигурировать параметры поиска и поведение ваших индексов AACSearch. Этот API предоставляет конечные точки для настройки того, как ранжируются, фильтруются и отображаются результаты поиска, чтобы оптимизировать поисковый опыт для ваших пользователей.

## Обзор

Настройки индекса контролируют различные аспекты функциональности поиска, такие как какие атрибуты доступны для поиска, как ранжируются результаты и как обрабатываются опечатки. API настроек позволяет точно настроить эти параметры под ваш конкретный сценарий использования.

- **Базовая конечная точка**: `/indexes/{name}/settings`
- **Аутентификация**: Требуется API-ключ, передаваемый в заголовке как `X-API-Key`.

## Получение настроек индекса

Получить текущие настройки для конкретного индекса.

- **Конечная точка**: `GET /indexes/{name}/settings`
- **Описание**: Возвращает полную конфигурацию настроек для указанного индекса.

### Запрос

```bash
curl -X GET "https://api.aacsearch.com/indexes/продукты/settings" \
  -H "X-API-Key: your-api-key"
```

### Ответ

```json
{
  "index": "продукты",
  "settings": {
    "searchableAttributes": ["title", "description", "brand"],
    "filterableAttributes": ["category", "price", "brand"],
    "sortableAttributes": ["price", "rating"],
    "ranking": ["words", "typo", "geo", "filters", "exact", "custom"],
    "customRanking": ["desc(price)"],
    "typoTolerance": {
      "enabled": true,
      "minWordSizeForTypos": {
        "oneTypo": 4,
        "twoTypos": 8
      }
    },
    "faceting": {
      "maxValuesPerFacet": 100
    },
    "pagination": {
      "hitsPerPage": 20
    },
    "highlighting": {
      "attributesToHighlight": ["title", "description"],
      "highlightPreTag": "<em>",
      "highlightPostTag": "</em>"
    },
    "synonyms": true,
    "queryLanguages": ["ru"]
  },
  "updatedAt": "2023-01-05T10:20:30Z"
}
```

## Обновление настроек индекса

Обновить настройки для конкретного индекса, чтобы настроить поведение поиска.

- **Конечная точка**: `PUT /indexes/{name}/settings`
- **Описание**: Обновляет настройки для указанного индекса. Обновляются только предоставленные поля; опущенные поля остаются без изменений.

### Запрос

```bash
curl -X PUT "https://api.aacsearch.com/indexes/продукты/settings" \
  -H "X-API-Key: your-api-key" \
  -H "Content-Type: application/json" \
  -d '{
    "searchableAttributes": ["title", "description", "brand", "category"],
    "filterableAttributes": ["category", "price", "brand", "availability"],
    "sortableAttributes": ["price", "rating", "releaseDate"],
    "ranking": ["words", "typo", "geo", "filters", "exact", "custom"],
    "customRanking": ["desc(price)", "desc(rating)"],
    "typoTolerance": {
      "enabled": true,
      "minWordSizeForTypos": {
        "oneTypo": 3,
        "twoTypos": 7
      }
    },
    "faceting": {
      "maxValuesPerFacet": 50
    },
    "pagination": {
      "hitsPerPage": 25
    },
    "highlighting": {
      "attributesToHighlight": ["title", "description", "brand"],
      "highlightPreTag": "<strong>",
      "highlightPostTag": "</strong>"
    },
    "queryLanguages": ["ru", "en"]
  }'
```

### Ответ

```json
{
  "index": "продукты",
  "status": "updated",
  "updatedAt": "2023-01-05T10:25:45Z",
  "settings": {
    "searchableAttributes": ["title", "description", "brand", "category"],
    "filterableAttributes": ["category", "price", "brand", "availability"],
    "sortableAttributes": ["price", "rating", "releaseDate"],
    "ranking": ["words", "typo", "geo", "filters", "exact", "custom"],
    "customRanking": ["desc(price)", "desc(rating)"],
    "typoTolerance": {
      "enabled": true,
      "minWordSizeForTypos": {
        "oneTypo": 3,
        "twoTypos": 7
      }
    },
    "faceting": {
      "maxValuesPerFacet": 50
    },
    "pagination": {
      "hitsPerPage": 25
    },
    "highlighting": {
      "attributesToHighlight": ["title", "description", "brand"],
      "highlightPreTag": "<strong>",
      "highlightPostTag": "</strong>"
    },
    "synonyms": true,
    "queryLanguages": ["ru", "en"]
  }
}
```

## Ключевые параметры настроек

Ниже приведены некоторые из наиболее важных настроек, которые вы можете конфигурировать через API настроек:

- **`searchableAttributes`**: Определяет, какие поля в ваших объектах доступны для поиска. Указывайте атрибуты в порядке важности для целей ранжирования. Пример: `["title", "description"]`.
- **`filterableAttributes`**: Указывает, какие атрибуты могут использоваться для фильтрации результатов поиска. Пример: `["category", "price"]`.
- **`sortableAttributes`**: Определяет атрибуты, которые могут использоваться для сортировки результатов поиска. Пример: `["price", "rating"]`.
- **`ranking`**: Указывает порядок критериев ранжирования для результатов поиска. Общие значения включают `words` (совпадение слов), `typo` (толерантность к опечаткам), `geo` (геолокация), `filters` (примененные фильтры), `exact` (точные совпадения) и `custom` (пользовательские правила). Пример: `["words", "typo", "geo", "filters", "exact", "custom"]`.
- **`customRanking`**: Пользовательские правила ранжирования для приоритизации определенных атрибутов (например, `desc(price)` для убывания цены). Пример: `["desc(price)", "asc(rating)"]`.
- **`typoTolerance`**: Контролирует, как обрабатываются опечатки в поисковых запросах. Вы можете включить/выключить это и установить пороги, когда опечатки допускаются. Пример: `{"enabled": true, "minWordSizeForTypos": {"oneTypo": 4, "twoTypos": 8}}`.
- **`faceting`**: Настраивает поведение фасетов, например, максимальное количество значений, возвращаемых для каждого фасета. Пример: `{"maxValuesPerFacet": 100}`.
- **`pagination`**: Устанавливает значения по умолчанию для пагинации, такие как количество результатов на странице. Пример: `{"hitsPerPage": 20}`.
- **`highlighting`**: Настраивает, как подсвечиваются совпадающие термины в результатах поиска. Пример: `{"attributesToHighlight": ["title"], "highlightPreTag": "<em>", "highlightPostTag": "</em>"}`.
- **`queryLanguages`**: Указывает языки для обработки запросов (например, для языково-специфического стемминга или стоп-слов). Пример: `["ru", "en"]`.
- **`synonyms`**: Включает поддержку синонимов для индекса. Установите в `true` для включения. Смотрите [Синонимы](../guides/search/synonyms.md) для подробной конфигурации.

## Лучшие практики конфигурации настроек

- **Приоритизация атрибутов для поиска**: Указывайте наиболее важные атрибуты первыми в `searchableAttributes`, чтобы влиять на ранжирование. Например, приоритизируйте `title` над `description`, если заголовки более релевантны для пользователей.
- **Оптимизация фильтрации**: Включайте в `filterableAttributes` только те атрибуты, которые необходимы для фильтрации, чтобы уменьшить размер индекса и повысить производительность.
- **Настройка ранжирования**: Используйте `ranking` и `customRanking` для настройки порядка результатов под ваш сценарий. Для электронной коммерции вы можете приоритизировать цену или популярность с помощью `customRanking: ["desc(popularity)"]`.
- **Обработка опечаток**: Настройте `typoTolerance` в зависимости от вашей аудитории. Для коротких запросов уменьшите пороги `minWordSizeForTypos`; для точных поисков рассмотрите возможность отключения.
- **Итеративное тестирование настроек**: Обновляйте настройки постепенно и отслеживайте влияние на релевантность и производительность поиска с помощью [API аналитики](./analytics.md).

## Устранение неисправностей

Если вы столкнулись с проблемами с настройками индекса:

- Убедитесь, что ваш API-ключ имеет необходимые разрешения для обновления настроек.
- Проверьте, что обновляемые настройки совместимы с вашей структурой данных (например, атрибуты, указанные в `searchableAttributes`, должны существовать в ваших объектах).
- Ознакомьтесь с разделом [Ошибки API](../troubleshooting/api-errors.md) для конкретных кодов ошибок и решений.
- Используйте [Режим отладки](../troubleshooting/debug.md) для получения подробных логов для диагностики проблем.

## Дополнительные ресурсы

- [Дашборд AACSearch](https://dashboard.aacsearch.com) - Настройка параметров визуально через дашборд.
- [Площадка API](https://api.aacsearch.com/playground) - Интерактивное тестирование вызовов API настроек.
- [Руководство по настройке поиска](../guides/dashboard/search-config.md) - Узнайте, как настраивать параметры поиска через дашборд.
- [Настройка релевантности](../guides/search/relevance.md) - Подробное руководство по оптимизации релевантности поиска с помощью настроек.
- [API аналитики](./analytics.md) - Используйте аналитику для оценки влияния изменений настроек.
