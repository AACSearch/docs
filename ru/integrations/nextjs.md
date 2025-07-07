# Next.js Integration для AACSearch

Этот документ описывает интеграцию AACSearch в приложения на Next.js для создания мощного поиска в ваших веб-приложениях.

## Установка

Инструкции по установке необходимых пакетов для интеграции AACSearch с Next.js.

```bash
npm install @aacsearch/next
```

## Настройка

Руководство по настройке AACSearch в приложении Next.js.

1. Создайте конфигурационный файл для AACSearch в вашем проекте.
2. Настройте API-ключ и индекс для поиска.

```javascript
// pages/_app.js
import { AACSearchProvider } from "@aacsearch/next";

function MyApp({ Component, pageProps }) {
  return (
    <AACSearchProvider apiKey="ваш-api-ключ" index="ваш-индекс">
      <Component {...pageProps} />
    </AACSearchProvider>
  );
}

export default MyApp;
```

## Использование

Описание того, как использовать AACSearch в компонентах Next.js.

- Интеграция поиска на страницах и в компонентах.
- Использование серверного рендеринга для оптимизации поиска.

## Дополнительные ресурсы

- [Официальная документация API](./../../api/quickstart.md)
- [Примеры кода](./../../examples/README.md)
