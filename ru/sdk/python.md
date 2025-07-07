# Python SDK для AACSearch

Этот документ описывает использование Python SDK для интеграции AACSearch на backend-уровне.

## Установка

Инструкции по установке Python SDK для AACSearch.

```bash
pip install aacsearch
```

## Инициализация

Пример кода для инициализации SDK с вашим API-ключом.

```python
# Пример инициализации AACSearch Python SDK
from aacsearch import AACSearch

client = AACSearch(api_key="ваш-api-ключ")
index = client.index("ваш-индекс")
```

## Основные функции

Описание ключевых функций Python SDK для управления индексами, добавления объектов и выполнения поисковых запросов.

## Примеры использования

Примеры кода для типичных сценариев использования на backend-е.

## Дополнительные ресурсы

- [Официальная документация API](./../../api/quickstart.md)
- [Примеры кода](./../../examples/README.md)
