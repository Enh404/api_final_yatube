# Описание проекта:

Данный проект это API версия блога Yatube. Теперь, с помощью различных запросов к эндпойнтам (например в Postman) можно получать информацию, которая содержится на сайте.

В данном проекте используются такие запросы:
- GET
- POST 
- PATCH 
- PUT 
- DELETE

Работа выполнена с помощью библиотек Django и Django Rest Framework (*DRF*). Для обработки запросов к API применяются Вьюсеты (*viewset*), к каждому из них написаны Сериализаторы (*serializers*). Роутинг запросов реализован с помощью *DefaultRouter* - одного из инструментов DRF. Так же в проекте предусмотрена аутентификация по *JWT*-токену. Права доступа для различных видов запросов отличаются, например чтение постов разрешено всем, а изенение - только автору поста. Это все заслуга различных пермишенов (*permissions*). Для более удобного и гибкого поиска постов исползуется пагинация, основанная на классе *LimitOffsetPagination* и поисковый бэкенд *SearchFilter*.

# Как запустить проект:

Клонировать репозиторий и перейти в него в командной строке:

`git clone git@github.com:Enh404/api_final_yatube.git`

`cd api_final_yatube`

Cоздать и активировать виртуальное окружение:

`python -m venv venv`

`. venv/Scripts/activate`

Установить зависимости из файла requirements.txt:

`python -m pip install --upgrade pip`

`pip install -r requirements.txt`

Выполнить миграции:

`python manage.py migrate`

Запустить проект:

`python manage.py runserver`

# Примеры запросов к API:

### GET-запрос

[http://127.0.0.1:8000/api/v1/posts/](url) - Получение списка всех публикаций.

### Пример ответа

`{
  "count": 123,
  "next": "http://api.example.org/accounts/?offset=400&limit=100",
  "previous": "http://api.example.org/accounts/?offset=200&limit=100",
  "results": [
    {
      "id": 0,
      "author": "string",
      "text": "string",
      "pub_date": "2021-10-14T20:41:29.648Z",
      "image": "string",
      "group": 0
    }
  ]
}`

### POST-запрос

[http://127.0.0.1:8000/api/v1/follow/](url)

### Пример запроса

`{
  "following": "string"
}`

### Пример ответа

`{
  "user": "string",
  "following": "string"
}`

### DELETE-запрос

[http://127.0.0.1:8000/api/v1/posts/{post_id}/comments/{id}/](url)

### Пример ответа (если вы не автор комментария)

`{
  "detail": "У вас недостаточно прав для выполнения данного действия."
}`

### Полная документация проекта доступна по ссылке:

[http://127.0.0.1:8000/redoc/](url)
