MMF использует `nginx` для распредления нагрузки как между своими репликами, так и между репликами 
с моделями. Чтобы запросы, касающиеся конкретной задачи, всегда попадли в строго опредленную реплику,
используется модуль [ngx_http_upstream_consistent_hash](https://www.nginx.com/nginx-wiki/build/dirhtml/modules/consistent_hash/), который определяет целевой сервер с помощью хеша от 
заданной переменной. Такой переменной является заголовок `TASK-ID`


Чтобы не создавать лишнюю нагрузку на центральный сервер MMF, `TASK-ID` формируется на стороне клиента. Ответсвенность 
за отсутсвие коллизий лежит так же на клиенте. MMF на своем клиенте использует uuid для генерации "безопасных" `TASK-ID`.
`TASK-ID` должны быть уникальны в рамках проекта. В случае обнаружения коллизии сервер с моделью отклоняет 
запрос на создание новой задачи.

Благодаря такому подходу, сервер с моделью может самостоятельно обсулижвать асинхронные запросы: создание задачи, 
мониторинг лога, загрузка результатов. Нет необходимости в централизированном управлении очередью задач. 