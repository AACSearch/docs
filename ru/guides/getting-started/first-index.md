# Первый индекс

Создание вашего первого поискового индекса - это важный шаг для начала использования AACSearch для организации и поиска ваших данных. Индекс - это контейнер для вашего содержимого, доступного для поиска, позволяющий эффективно хранить и извлекать данные. Это руководство проведет вас через процесс настройки вашего первого индекса с помощью Панели управления AACSearch.

## Предварительные условия

Перед созданием индекса убедитесь, что вы выполнили следующие условия:

- **Настройка аккаунта**: У вас есть активный аккаунт AACSearch. Если нет, следуйте руководству [Настройка аккаунта](../getting-started/account-setup.md).
- **Доступ к панели управления**: Войдите в [Панель управления AACSearch](https://dashboard.aacsearch.com) с вашими учетными данными.

## Шаг 1: Перейдите к индексам

После входа в Панель управления AACSearch:

1. **Найдите раздел Индексы**: В боковой панели слева нажмите на "Индексы". Этот раздел предназначен для управления всеми вашими поисковыми индексами.
2. **Просмотрите список индексов**: Если вы делаете это впервые, список будет пустым. Вы увидите приглашение создать ваш первый индекс.

## Шаг 2: Создайте новый индекс

Чтобы создать ваш первый индекс:

1. **Нажмите на Создать индекс**: В правом верхнем углу страницы Индексы нажмите кнопку "Создать индекс".
2. **Назовите ваш индекс**: В появившемся диалоговом окне введите уникальное имя для вашего индекса. Используйте описательное имя, отражающее данные, которые он будет содержать (например, "продукты" для каталога электронной коммерции или "статьи" для блога).
   - **Примечание**: Имена индексов должны быть в нижнем регистре, алфавитно-цифровыми и могут включать дефисы (например, "my-products-index"). Пробелы и специальные символы не допускаются.
3. **Установите основной язык (Необязательно)**: Выберите основной язык для содержимого в этом индексе. Это помогает AACSearch оптимизировать поиск для языково-специфических функций, таких как стемминг и стоп-слова. Вы можете изменить это позже.
4. **Подтвердите создание**: Нажмите "Создать", чтобы завершить настройку. Ваш новый индекс появится в списке.

## Шаг 3: Настройте базовые параметры

После создания индекса вы можете настроить его базовые параметры, чтобы адаптировать поведение поиска:

1. **Выберите ваш индекс**: Нажмите на только что созданный индекс из списка, чтобы открыть страницу его конфигурации.
2. **Определите атрибуты для поиска**: Во вкладке "Схема" или "Настройки" укажите, какие поля в ваших данных должны быть доступны для поиска. Например, если ваши данные включают "title" и "description", добавьте их как атрибуты для поиска.
   - **Совет**: Приоритизируйте важные поля (например, "title"), указывая их первыми, так как это может влиять на ранжирование.
3. **Установите атрибуты для фильтрации (Необязательно)**: Определите поля, которые могут использоваться для фильтрации результатов (например, "category" или "price"). Это полезно для сужения результатов поиска.
4. **Сохраните изменения**: Нажмите "Сохранить настройки", чтобы применить вашу конфигурацию. Эти настройки можно будет скорректировать позже по мере необходимости.

## Шаг 4: Подтвердите создание индекса

Чтобы убедиться, что ваш индекс готов:

1. **Проверьте статус**: Вернитесь к списку Индексов в панели управления. Ваш индекс должен показывать статус "Активен" или "Готов".
2. **Просмотрите детали**: Нажмите на индекс, чтобы увидеть его детали, включая количество объектов (на данный момент 0, так как данные еще не добавлены) и сводку конфигурации.

## Следующие шаги

С созданным первым индексом вы готовы заполнить его данными и интегрировать функциональность поиска в ваше приложение:

- **[Загрузка данных](../getting-started/data-upload.md)**: Узнайте, как добавить данные в ваш индекс для поиска.
- **[Интеграция](../getting-started/integration.md)**: Интегрируйте AACSearch в ваше приложение или веб-сайт, чтобы включить поиск.
- **[Настройка поиска](../dashboard/search-config.md)**: Изучите продвинутые настройки для точной настройки релевантности и производительности поиска.

## Устранение неисправностей

Если вы столкнулись с проблемами при создании вашего первого индекса:

- **Ошибки именования**: Убедитесь, что имя индекса соответствует требуемому формату (нижний регистр, алфавитно-цифровой, только дефисы). Если имя уже используется, выберите другое.
- **Проблемы с разрешениями**: Проверьте, что ваш аккаунт или API-ключ имеет необходимые разрешения для создания индексов. Если нет, свяжитесь с администратором вашей организации или поддержкой.
- **Панель управления не отвечает**: Если панель управления работает медленно или не отвечает, обновите страницу или проверьте ваше интернет-соединение. Если проблема сохраняется, сообщите об этом на support@aacsearch.com.
- **Свяжитесь с поддержкой**: Для дальнейшей помощи обратитесь в нашу службу поддержки через [community.aacsearch.com](https://community.aacsearch.com) или по email support@aacsearch.com.

## Дополнительные ресурсы

- [Панель управления AACSearch](https://dashboard.aacsearch.com) - Управляйте вашими индексами и настройками.
- [Управление индексами](../dashboard/indexes.md) - Узнайте больше об управлении индексами через панель управления.
- [Справочник API по индексам](../../api/index.md) - Используйте API для программного создания и управления индексами.
- [Форум сообщества](https://community.aacsearch.com) - Общайтесь с другими пользователями для получения советов и устранения неполадок.
