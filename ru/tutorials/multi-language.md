# Многоязычный поиск с AACSearch

Этот туториал поможет вам шаг за шагом настроить многоязычный поиск с использованием AACSearch.

## Предварительные требования

Перед началом убедитесь, что у вас есть:

- Аккаунт AACSearch с настроенным API-ключом.
- Доступ к панели управления AACSearch.
- Контент на нескольких языках для индексации.

## Шаг 1: Создание индексов для разных языков

Настройка отдельных индексов для каждого языка.

1. Перейдите в панель управления AACSearch.
2. Создайте новый индекс для каждого языка (например, "products_en", "products_ru").
3. Загрузите соответствующие данные в каждый индекс.

## Шаг 2: Настройка параметров языка

Укажите языковые настройки для каждого индекса.

1. В настройках индекса выберите язык для обработки текста (например, "English" для "products_en").
2. Настройте параметры обработки текста, такие как стоп-слова и синонимы, специфичные для языка.

## Шаг 3: Определение языка пользователя

Определите язык пользователя для выбора правильного индекса.

```javascript
// Определение языка пользователя на основе настроек браузера
const userLanguage = navigator.language.split("-")[0]; // Например, "en" или "ru"
const indexName = `products_${userLanguage}`;

// Инициализация поиска с выбранным индексом
const search = new AACSearch({
  apiKey: "ваш-api-ключ",
  index: indexName,
});
```

## Шаг 4: Интеграция с интерфейсом

Настройте интерфейс для переключения языков вручную, если необходимо.

```html
<select id="languageSelect">
  <option value="en">English</option>
  <option value="ru">Русский</option>
</select>
<input type="text" id="searchInput" placeholder="Введите поисковый запрос..." />
<div id="searchResults"></div>
```

```javascript
document
  .getElementById("languageSelect")
  .addEventListener("change", function (e) {
    const selectedLanguage = e.target.value;
    const indexName = `products_${selectedLanguage}`;

    const search = new AACSearch({
      apiKey: "ваш-api-ключ",
      index: indexName,
    });

    // Переинициализация поиска с новым индексом
    document
      .getElementById("searchInput")
      .addEventListener("input", function (e) {
        search.query(e.target.value).then((results) => {
          const resultsContainer = document.getElementById("searchResults");
          resultsContainer.innerHTML = results
            .map((result) => `<div>${result.title}</div>`)
            .join("");
        });
      });
  });
```

## Шаг 5: Тестирование многоязычного поиска

Проверьте, что поиск работает корректно для каждого языка.

- Переключите язык и выполните поисковые запросы.
- Убедитесь, что результаты соответствуют выбранному языку.

## Дополнительные ресурсы

- [Официальная документация API](./../api/quickstart.md)
- [Примеры кода](./../examples/README.md)
