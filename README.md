# yamdb_final
yamdb_final

![example workflow](https://github.com/korshikovvital/yamdb_final/actions/workflows/yamdb_workflow.yml/badge.svg)

# Описание:
Этот проект собирает отзывы на произведения. Аутентифицированные пользователи могут оставлять отзывы на произведения, добавленные администраторами проекта. Пользователи также могут оставлять комментарии к отзывам.
IP 158.160.60.131

# Как запустить проект:
Клонировать репозиторий и перейти в него в командной строке:

Из папки infra/ соберите образ при помощи

`docker-compose $ docker-compose up -d --build`

Примените миграции 

`$ docker-compose exec web python manage.py migrate`

Соберите статику

`$ docker-compose exec web python manage.py collectstatic --no-input`

Для доступа к админке не забудьте создать суперюзера

`$ docker-compose exec web python manage.py createsuperuser`

`
Пример ответа:
{
    "count": 3,
    "next": null,
    "previous": null,
    "results": [
        {
            "name": "Фильм",
            "slug": "movie"
        },
        ...
    ]
}

POST .../api/v1/titles/1/reviews/

{
    "text": "Тест",
    "score": 10
}
Пример ответа:

{
    "id": 1,
    "text": "Тест",
    "author": "admin",
    "score": 10,
    "pub_date": "2022-10-24T08:29:12.186741Z"
}
PATCH .../api/v1/titles/1/reviews/1/comments/1

{
    "text": "Комментарий"
}
Пример ответа:

{
    "id": 1,
    "text": "Комментарий",
    "author": "admin",
    "pub_date": "2022-10-24T09:04:42.770603Z"
}
`
