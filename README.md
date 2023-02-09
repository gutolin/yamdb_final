# Yamdb

![yamdb main branch](https://github.com/gutolin/yamdb_final/actions/workflows/yamdb_workflow.yml/badge.svg)

Ресурс отзывов на фильмы, музыку и книги

Текущий адресс проекта: http://51.250.29.83

## Как развернуть проект

- Установить актуальную версию [docker'a](https://www.docker.com)
- В терминале развернуть контейнер из дерриктории **api_yamdb**
```sh
docker build -t <container-name> .
```
- Установить зависимости из файла **docker-compose** в дерриктории **infra** 
```sh
docker-compose up
```
- Применить миграции
```sh
docker-compose exec <container-name> python manage.py migrate
```
- Создать суперпользователя
```sh
docker-compose exec <container-name> python manage.py createsuperuser
```
- Собрать статику проекта
```sh
docker-compose exec <container-name> python manage.py collectstatic --no-input
```
- Загрузить данные в бд из фикстур
```sh
python manage.py loaddata infra/fixtures.json
```
## Шаблон заполнения .env файла. Сам файл в репозитории отсутствует. Добавить по пути infra/.env

- Тип БД
```sh
DB_ENGINE=django.db.backends.postgresql
```
- Имя БД
```sh
DB_NAME=postgres
```
- Логин пароль для подключения к БД
```sh
POSTGRES_USER=postgres
POSTGRES_PASSWORD=postgres
```
- Название контейнера
```sh
DB_HOST=db
```
- Порт для подключения к БД
```sh
DB_PORT=5432
```
