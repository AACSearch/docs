# Автодополнение

Это руководство объясняет, как настроить и управлять функцией автодополнения в AACSearch, чтобы помочь пользователям быстрее находить контент, предлагая поисковые термины по мере ввода.

## Введение

Автодополнение, также известное как предиктивный ввод или поиск по мере набора, предсказывает и предлагает поисковые термины или фразы на основе ввода пользователя в реальном времени. AACSearch предоставляет мощные инструменты для реализации автодополнения, улучшая пользовательский опыт за счет сокращения усилий на ввод текста и направления пользователей к релевантному контенту.

## Доступ к настройкам автодополнения

1. **Перейдите к индексам**: В боковом меню дашборда выберите "Индексы".
2. **Выберите индекс**: Нажмите на индекс, который вы хотите настроить.
3. **Перейдите к настройкам поиска**: В деталях индекса найдите вкладку или раздел "Настройка поиска", затем ищите настройки "Автодополнение" или "Предложения запросов".

## Понимание автодополнения

- **Предложения запросов**: Предложения, основанные на популярных или трендовых поисковых терминах в вашем индексе.
- **Предложения дополнения**: Предложения, которые завершают частичный ввод пользователя на основе проиндексированного контента (например, предложение "смартфон", когда пользователь вводит "смарт").
- **Динамические результаты**: По мере ввода текста автодополнение может отображать не только термины, но и прямые результаты или предварительный просмотр совпадающего контента.

## Настройка автодополнения

1. **Включите автодополнение**: В настройках автодополнения включите эту функцию для вашего индекса.
2. **Настройте источники предложений**:
   - **Проиндексированный контент**: Основывайте предложения на реальных данных в вашем индексе (например, заголовки, ключевые слова).
   - **История запросов**: Используйте исторические данные поиска для предложения популярных запросов.
   - **Пользовательские предложения**: Вручную определите список терминов или фраз для предложения, полезно для акций или ключевого контента.
3. **Установите параметры отображения**:
   - **Количество предложений**: Ограничьте количество отображаемых предложений, чтобы не перегружать пользователей (например, 5-10 предложений).
   - **Задержка и триггер**: Установите задержку ввода или минимальное количество символов перед появлением предложений (например, после 3 символов или паузы в 200 мс).
   - **Категории**: Сгруппируйте предложения по категориям (например, "Продукты", "Категории"), если это применимо.
4. **Сохраните изменения**: Примените ваши настройки, чтобы обновить индекс с новой конфигурацией автодополнения.

## Настройка поведения автодополнения

- **Подсветка совпадений**: Подсвечивайте совпадающую часть предложений, чтобы показать пользователям, как их ввод связан с предложением.
- **Персонализация**: Настраивайте предложения на основе контекста пользователя, такого как местоположение или прошлые поиски, если это поддерживается вашей настройкой.
- **Фильтрация предложений**: Ограничьте предложения конкретными полями или фасетами (например, предлагайте только названия продуктов, а не описания).

## Интеграция автодополнения в интерфейс

- **Виджеты автодополнения**: Используйте SDK или компоненты AACSearch (например, JavaScript SDK, компоненты React) для интеграции автодополнения в вашу поисковую строку или интерфейс.
- **Пользовательская стилизация**: Настройте стиль выпадающего списка предложений, чтобы он соответствовал дизайну вашего приложения, обеспечивая бесшовный пользовательский опыт.
- **Навигация с клавиатуры**: Разрешите пользователям перемещаться по предложениям с помощью стрелок на клавиатуре и выбирать с помощью Enter для доступности.

## Тестирование автодополнения

- **Предпросмотр поиска**: Используйте инструмент предпросмотра поиска в дашборде, чтобы протестировать предложения автодополнения с различными частичными запросами.
- **Анализируйте аналитику**: Отслеживайте аналитику, чтобы увидеть, как часто пользователи взаимодействуют с предложениями автодополнения и приводят ли они к успешным поискам.
- **Итерируйте**: Корректируйте настройки автодополнения на основе поведения пользователей, чтобы приоритизировать наиболее полезные предложения.

## Лучшие практики

- **Держите предложения релевантными**: Убедитесь, что предложения тесно связаны с намерением пользователя, приоритизируя высококачественный проиндексированный контент или популярные запросы.
- **Оптимизируйте скорость**: Автодополнение должно реагировать мгновенно; минимизируйте задержку предложений, ограничивая количество результатов или кэшируя распространенные запросы.
- **Избегайте беспорядка**: Отображайте краткий список предложений, чтобы предотвратить усталость от принятия решений; сосредоточьтесь на наиболее вероятных совпадениях.
- **Поддерживайте многоязычность**: Если ваш поиск поддерживает несколько языков, настройте автодополнение для предложения терминов на языке пользователя.

## Продвинутое использование автодополнения

- **Предложения через API**: Используйте API AACSearch для программного получения предложений автодополнения для пользовательских интерфейсов или потребностей в реальном времени.
- **Пользовательское ранжирование**: Определите пользовательскую логику для ранжирования предложений автодополнения помимо стандартной релевантности (требуется продвинутая настройка).
- **Машинное обучение**: Используйте машинное обучение для улучшения точности предложений со временем на основе взаимодействий пользователей.

## Устранение неисправностей

- **Предложения не отображаются**: Убедитесь, что автодополнение включено и что в индексе достаточно контента или истории запросов для генерации предложений.
- **Нерелевантные предложения**: Проверьте источник предложений (например, проиндексированные поля, пользовательский список) и уточните, чтобы сосредоточиться на релевантных данных.
- **Медленный отклик**: Если предложения загружаются медленно, уменьшите количество предложений или оптимизируйте индекс для более быстрого поиска.
- **Свяжитесь с поддержкой**: Для сложных вопросов с автодополнением обратитесь в поддержку через [community.aacsearch.com](https://community.aacsearch.com) или по email support@aacsearch.com.

## Следующие шаги

- Узнайте о настройке релевантности в [Настройка релевантности](../search/relevance.md).
- Изучите управление синонимами в [Синонимы](../search/synonyms.md).
- Погрузитесь глубже в фасетный поиск с [Фасетный поиск](../search/facets.md).

## Дополнительные ресурсы

- [Дашборд AACSearch](https://dashboard.aacsearch.com) - Доступ к вашему аккаунту и управление настройками.
- [Форум сообщества](https://community.aacsearch.com) - Общайтесь с другими пользователями и получайте помощь.
