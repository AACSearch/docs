# Mobile SDKs для AACSearch

Этот документ описывает использование SDK для мобильных приложений на iOS и Android для интеграции AACSearch.

## Установка

Инструкции по установке Mobile SDKs для AACSearch.

### iOS

Инструкции для интеграции в приложения на Swift или Objective-C.

### Android

Инструкции для интеграции в приложения на Kotlin или Java.

## Инициализация

Пример кода для инициализации SDK в мобильных приложениях.

### iOS (Swift)

```swift
// Пример инициализации AACSearch iOS SDK
import AACSearch

let client = AACSearch(apiKey: "ваш-api-ключ")
let index = client.index("ваш-индекс")
```

### Android (Kotlin)

```kotlin
// Пример инициализации AACSearch Android SDK
import com.aacsearch.AACSearch

val client = AACSearch(apiKey = "ваш-api-ключ")
val index = client.index("ваш-индекс")
```

## Основные функции

Описание ключевых функций Mobile SDKs для выполнения поиска и других операций в мобильных приложениях.

## Примеры использования

Примеры кода для типичных сценариев использования в мобильных приложениях.

## Дополнительные ресурсы

- [Официальная документация API](./../../api/quickstart.md)
- [Примеры кода](./../../examples/README.md)
