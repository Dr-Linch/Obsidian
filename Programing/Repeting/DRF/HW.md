# Lesson #1

### Task #1
Создайте новый Django-проект, подключите DRF в настройках проекта.

### Task #2
Создайте следующие модели:

1. Пользователь:
- все поля от обычного пользователя, но авторизацию заменить на email;
- телефон;
- город;
- аватарка.
Модель пользователя разместите в приложении users

2. Курс:
- название,
- превью (картинка),
- описание.

3. Урок:
- название,
- описание,
- превью (картинка),
- ссылка на видео.

>Урок и курс - это связанные между собой сущности. Уроки складываются в курс, в одном курсе может быть много уроков. Реализуйте связь между ними.

Модель курса и урока разместите в отдельном приложении. Название для приложения выбирайте такое, чтобы оно описывало то, с какими сущностями приложение работает. Например, lms или materials - отличные варианты.

### Task #3
Опишите CRUD для моделей курса и урока. Для реализации CRUD для курса используйте Viewsets, а для урока - Generic-классы.
Для работы контроллеров опишите простейшие сериализаторы.

>При реализации CRUD для уроков реализуйте все необходимые операции (получение списка, получение одной сущности, создание, изменение и удаление).

Для работы контроллеров опишите простейшие сериализаторы.

>Работу каждого эндпоинта необходимо проверять с помощью Postman.
Также на данном этапе работы мы не заботимся о безопасности и не закрываем от редактирования объекты и модели даже самой простой авторизацией.

### \* Task #4
Реализуйте эндпоинт для редактирования профиля любого пользователя на основе более привлекательного подхода для личного использования: Viewset или Generic.

# Lesson #2

### Task #1
Для модели курса добавьте в сериализатор поле вывода количества уроков. Поле реализуйте с помощью 
```
SerializerMethodField()
```

### Task #2
Добавьте новую модель в приложение users:

Платежи:
- пользователь,
- дата оплаты,
- оплаченный курс или урок,
- сумма оплаты,
- способ оплаты: наличные или перевод на счет.

>Поля 
```
пользователь
```
, 
```
оплаченный курс
```
 и 
```
отдельно оплаченный урок
```
 должны быть ссылками на соответствующие модели.

Запишите в таблицу, соответствующую этой модели данные через инструмент фикстур или кастомную команду.

>Если вы забыли как работать с фикстурами или кастомной командой - можете вернуться к уроку 20.1 Работа с ORM в Django чтобы вспомнить материал.

### Task #3
Для сериализатора для модели курса реализуйте поле вывода уроков. Вывод реализуйте с помощью сериализатора для связанной модели.

>Один сериализатор должен выдавать и количество уроков курса и информацию по всем урокам курса одновременно.

### Task #4
Настроить фильтрацию для эндпоинта вывода списка платежей с возможностями:
- менять порядок сортировки по дате оплаты,
- фильтровать по курсу или уроку,
- фильтровать по способу оплаты.

>### Дополнительное задание
Для профиля пользователя сделайте вывод истории платежей, расширив сериализатор для вывода списка платежей

# Lesson #3

### Task #1
Настройте в проекте использование JWT-авторизации и закройте каждый эндпоинт авторизацией.

### Task #2
Заведите группу модераторов и опишите для нее права работы с любыми уроками или курсами, но без возможности их удалять и создавать новые. Заложите функционал такой проверки в контроллеры.

### Task #3
Опишите права доступа для объектов таким образом, чтобы пользователи, которые не входят в группу модераторов, могли видеть и редактировать только свои курсы и уроки.

>Заводить группы лучше через админку и не реализовывать для этого дополнительных эндпоинтов.

### \* Task #4
Для профиля пользователя введите ограничения, чтобы авторизованный пользователь мог просматривать любой профиль, но редактировать только свой. При этом при просмотре чужого профиля должна быть доступна только общая информация, в которую не входят: пароль, фамилия, история платежей.

# Lesson #4

### Task #1
Для сохранения уроков и курсов реализуйте дополнительную проверку на отсутствие в материалах ссылок на сторонние ресурсы, кроме youtube.com.

То есть ссылки на видео можно прикреплять в материалы, а ссылки на сторонние образовательные платформы или личные сайты — нельзя.

>Создайте отдельный файл 
```
validators.py
```
, реализуйте валидатор, проверяющий ссылку, которую пользователь хочет записать в поле урока с помощью класса или функции.
Интегрируйте валидатор в сериализатор.
Если вы используете функцию-валидатор — указанием валидаторов для поля сериализатора 
```
validators=[ваш_валидатор]
```
.
Если вы используете класс-валидатор — указанием валидаторов в 
```
class Meta
```
:
```
validators = [ваш_валидатор(field='поле_которое_валидируем')]
```
.

### Task #2
Добавьте модель подписки на обновления курса для пользователя.

>Модель подписки должна содержать следующие поля: «пользователь» (
```
FK
```
 на модель пользователя), «курс» (
```
FK
```
 на модель курса). Можете дополнительно расширить модель при необходимости.

Вам необходимо реализовать эндпоинт для установки подписки пользователя и на удаление подписки у пользователя.

При этом при выборке данных по курсу пользователю необходимо присылать признак подписки текущего пользователя на курс. То есть давать информацию, подписан пользователь на обновления курса или нет.

### Task #3
Реализуйте пагинацию для вывода всех уроков и курсов.

>Пагинацию реализуйте в отдельном файле 
```
paginators.py
```
. Можно реализовать один или несколько классов пагинатора. Укажите параметры 
```
page_size
```
, 
```
page_size_query_param
```
, 
```
max_page_size
```
 для класса 
```
PageNumberPagination
```
. Количество элементов на странице выберите самостоятельно. Интегрируйте пагинатор в контроллеры, используя параметр 
```
pagination_class
```
.

### Task #4
Напишите тесты, которые будут проверять корректность работы CRUD уроков и функционал работы подписки на обновления курса.

>В тестах используйте метод 
```
setUp
```
 для заполнения базы данных тестовыми данными. Обработайте возможные варианты взаимодействия с контроллерами пользователей с разными правами доступа. Для аутентификации пользователей используйте 
```
self.client.force_authenticate()
```
. Документацию к этому методу можно найти [тут](https://www.django-rest-framework.org/api-guide/testing/#forcing-authentication).

Сохраните результат проверки покрытия тестами.

>### Дополнительное задание
Напишите тесты на все имеющиеся эндпоинты в проекте.

# Lesson #5

### Task #1
Подключить и настроить вывод документации для проекта. Убедиться, что каждый из реализованных эндпоинтов описан в документации верно, при необходимости описать вручную.

>Для работы с документацией проекта воспользуйтесь библиотекой [drf-yasg](https://drf-yasg.readthedocs.io/en/stable/) или [drf-spectacular](https://drf-spectacular.readthedocs.io/en/latest/).
Как вручную можно сформировать документацию в drf-yasg можно почитать [тут](https://drf-yasg.readthedocs.io/en/stable/custom_spec.html), в drf-spectacular — [тут](https://habr.com/ru/articles/733942/) или [тут](https://drf-spectacular.readthedocs.io/en/latest/customization.html).

### Task #2
Подключить возможность оплаты курсов через [https://stripe.com/docs/api](https://stripe.com/docs/api).

Доступы можно получить напрямую из документации, а также пройти простую регистрацию по адресу [https://dashboard.stripe.com/register](https://dashboard.stripe.com/register).

>Для работы с учебным проектом достаточно зарегистрировать аккаунт и не подтверждать его — аккаунт будет находиться в тестовом режиме.

Для работы с запросами вам понадобится реализовать обращение к эндпоинтам:

- [https://stripe.com/docs/api/products/create](https://stripe.com/docs/api/products/create) — создание продукта;
- [https://stripe.com/docs/api/prices/create](https://stripe.com/docs/api/prices/create) — создание цены;
- [https://stripe.com/docs/api/checkout/sessions/create](https://stripe.com/docs/api/checkout/sessions/create) — создание сессии для получения ссылки на оплату.

>При создании цены и сессии обратите внимание на поля, которые вы передаете в запросе. Внимательно изучите значение каждого поля и проанализируйте ошибки при их возникновении, чтобы создать корректную запись.
При создании сессии нужно передавать id цены, которая соответствует конкретному продукту.

Для тестирования можно использовать номера карт из документации:

- [https://stripe.com/docs/terminal/references/testing#standard-test-cards](https://stripe.com/docs/terminal/references/testing#standard-test-cards).

>Примечание
Подключение оплаты лучше всего рассматривать как обычную задачу подключения к стороннему API.
Основной путь: запрос на покупку → оплата. Статус проверять не нужно.
Каждый эквайринг предоставляет тестовые карты для работы с виртуальными деньгами.

### \* Task #3
Реализуйте проверку статуса с помощью эндпоинта [https://stripe.com/docs/api/checkout/sessions/retrieve](https://stripe.com/docs/api/checkout/sessions/retrieve) — получение данных о сессии по идентификатору.

# Lesson #6

### Task #1
Настройте проект для работы с Celery. Также настройте приложение на работу с celery-beat для выполнения периодических задач.

>Не забудьте вынести настройки Redis в переменные окружения.

### Task #2
Ранее вы реализовали функционал подписки на обновление курсов. Теперь добавьте асинхронную рассылку писем пользователям об обновлении материалов курса.

>Чтобы реализовать асинхронную рассылку, вызывайте специальную задачу по отправке письма в коде контроллера. То есть вызов задачи на отправку сообщения должен происходить в контроллере обновления курса: когда курс обновлен — тем, кто подписан на обновления именно этого курса, отправляется письмо на почту.

### \* Task #3
Пользователь может обновлять каждый урок курса отдельно. Добавьте проверку на то, что уведомление отправляется только в том случае, если курс не обновлялся более четырех часов.

### Task #4
С помощью celery-beat реализуйте фоновую задачу, которая будет проверять пользователей по дате последнего входа по полю 
```
last_login
```
 и, если пользователь не заходил более месяца, блокировать его с помощью флага 
```
is_active
```
.

>Задачу сделайте периодической и запланируйте расписание в настройках celery-beat.
Обратите внимание на timezone вашего приложения и timezone в настройках celery: важно, чтобы они были одинаковыми, чтобы задачи запускались в корректное время.