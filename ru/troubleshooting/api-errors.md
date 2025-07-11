# Ошибки API с AACSearch

Этот документ описывает распространенные ошибки API, с которыми сталкиваются пользователи AACSearch, и способы их устранения.

## Ошибка 1: Invalid API Key (401 Unauthorized)

**Описание**: Запрос отклонен из-за недействительного или отсутствующего API-ключа.

**Решение**:

1. Проверьте, правильно ли указан API-ключ в заголовке запроса `X-API-Key`.
2. Убедитесь, что API-ключ не истек и не был отозван.
3. Сгенерируйте новый API-ключ в панели управления AACSearch, если текущий недействителен (см. [API Key Management](./../guides/security/api-keys.md)).

## Ошибка 2: Rate Limit Exceeded (429 Too Many Requests)

**Описание**: Вы превысили лимит запросов для вашего плана AACSearch.

**Решение**:

1. Проверьте текущие лимиты запросов для вашего плана в панели управления.
2. Внедрите ограничение скорости на клиентской стороне (см. [Rate Limiting](./../guides/security/rate-limiting.md)).
3. Рассмотрите обновление плана для увеличения лимита запросов.

## Ошибка 3: Index Not Found (404 Not Found)

**Описание**: Указанный индекс не существует или недоступен.

**Решение**:

1. Проверьте правильность имени индекса в запросе.
2. Убедитесь, что индекс был создан в панели управления AACSearch.
3. Проверьте права доступа к индексу, если используете ограниченные API-ключи.

## Ошибка 4: Invalid Query Parameters (400 Bad Request)

**Описание**: Запрос содержит некорректные параметры или синтаксис.

**Решение**:

1. Проверьте документацию API на предмет правильного формата параметров (см. [Search API](./../api/search.md)).
2. Убедитесь, что все обязательные параметры указаны.
3. Используйте инструменты отладки, такие как API Playground, для проверки запросов.

## Дополнительные ресурсы

- [Официальная документация API](./../api/quickstart.md)
- [Примеры кода](./../examples/README.md)
