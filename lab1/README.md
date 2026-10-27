
Останин Андрей 

Григорьев Максим 

Левахин Лев 

Сигаева Ксения 

Афанасьев Дмитрий 

# lab1

## запуск

Нужны Docker с Compose v2 и интернет. Порты 5432, 5433, 5434, 7000 и 2181 должны быть свободны.

Откройте терминал в папке с `docker-compose.yml` и выполните:

```sh
docker compose up -d --build
docker compose ps
docker exec pg-master patronictl -c /postgres0.yml list
```

Дождитесь состояния running у Leader и streaming у Sync Standby.

Подключение к базе через HAProxy:

```sh
docker exec -it -e PGPASSWORD=postgres pg-master psql -h haproxy -U postgres -d postgres
```

База, логин и пароль: `postgres` / `postgres` / `postgres`. Статистика HAProxy доступна по адресу http://localhost:7000.

Остановка с сохранением данных:

```sh
docker compose stop
```

Повторный запуск:

```sh
docker compose start
```
