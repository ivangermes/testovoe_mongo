## Что это

Микросервис, возвращает статистику по проданным заказам (status = "done") сгруппированные по каналам продаж (поле origin).
Работает с существующей коллекцией MongoDB.

## Endpoints
`/health` -  проверка живучести, только GET.

`/v1/origins_stats` - возвращает статистику, принимает как GET, так и POST запросы.

## Ответ
Результат возвращается в JSON формате.

Пример ответа:
```
[
    {
        origin: "widget",   # название канала
        tickets: 3,         # сколько билетов продано по этому каналу
        total: 237          # сумма продаж по каналу
    },
    ...
]
```

## Параметры

`time_from`, `time_to` - с какого и по какое время учитываются заказы.

Должны быть в формате ISO 8601.

Каждый из этих параметров необязательный.

Параметры могут передаватся как в GET, так и в POST запросах.

## Примеры запросов ( методом GET ):

`/v1/origins_stats` - статистика за все время

`/v1/origins_stats?time_from=2020-04-06T23:27:54.000Z&time_to=2023-04-08T07:11:04.000Z` - статистика с .. по ...

`/v1/origins_stats?time_from=2020-04-06T23:27:54.000Z`

`/v1/origins_stats?time_to=2023-04-08T07:11:04.000Z`

## Проверка живучести
`/health` - ответ `HEALTHY`, если все нормально и есть доступ к базе

## Окружение для запуска
`DB_NAME` - имя базы

`COLLECTION_NAME` - имя коллекции с заказами

`MONGO_URI`








