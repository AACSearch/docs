# Реализация автодополнения с AACSearch

Этот туториал поможет вам шаг за шагом реализовать функцию автодополнения с использованием AACSearch.

## Предварительные требования

Перед началом убедитесь, что у вас есть:

- Аккаунт AACSearch с настроенным API-ключом.
- Базовые знания HTML, CSS и JavaScript.

## Шаг 1: Подключение AACSearch SDK

Инструкции по подключению SDK к вашему проекту.

```html
<script src="https://cdn.aacsearch.com/aacsearch.min.js"></script>
```

## Шаг 2: Инициализация поиска

Настройка базового поиска с использованием AACSearch.

```javascript
const search = new AACSearch({
  apiKey: "ваш-api-ключ",
  index: "ваш-индекс",
});
```

## Шаг 3: Создание поля автодополнения

Добавление поля ввода для автодополнения запросов.

```html
<input
  type="text"
  id="autocompleteInput"
  placeholder="Введите поисковый запрос..."
/>
<div id="autocompleteSuggestions" style="display: none;"></div>
```

## Шаг 4: Реализация автодополнения

Привязка событий ввода для отображения подсказок автодополнения.

```javascript
const input = document.getElementById("autocompleteInput");
const suggestions = document.getElementById("autocompleteSuggestions");

input.addEventListener("input", function (e) {
  search.autocomplete(e.target.value).then((results) => {
    if (results.length > 0) {
      suggestions.innerHTML = results
        .map((result) => `<div class="suggestion">${result}</div>`)
        .join("");
      suggestions.style.display = "block";
    } else {
      suggestions.style.display = "none";
    }
  });
});

// Скрытие подсказок при клике вне поля
document.addEventListener("click", function (e) {
  if (e.target !== input) {
    suggestions.style.display = "none";
  }
});

// Выбор подсказки при клике
suggestions.addEventListener("click", function (e) {
  if (e.target.classList.contains("suggestion")) {
    input.value = e.target.textContent;
    suggestions.style.display = "none";
    // Выполнение поиска с выбранным значением
    search.query(input.value).then((results) => {
      // Обработка результатов поиска
    });
  }
});
```

## Шаг 5: Стилизация автодополнения

Добавление CSS для улучшения внешнего вида поля автодополнения и подсказок.

```css
#autocompleteInput {
  width: 100%;
  padding: 10px;
  font-size: 16px;
}

#autocompleteSuggestions {
  position: absolute;
  width: 100%;
  background: white;
  border: 1px solid #ddd;
  border-radius: 4px;
  max-height: 200px;
  overflow-y: auto;
  z-index: 1000;
}

.suggestion {
  padding: 10px;
  cursor: pointer;
}

.suggestion:hover {
  background-color: #f0f0f0;
}
```

## Дополнительные ресурсы

- [Официальная документация API](./../api/quickstart.md)
- [Примеры кода](./../examples/README.md)
