### Запуск проекта: 

 - Создать виртуальное окружение, установить зависимости, поменять значения в `orders/.env`
 - Создать базу данных:
```bash
createdb -U postgres diploma
```
 - Провести миграции:
```bash
python orders/manage.py migrate
```
Для silk:
```bash
python orders/manage.py collectstatic
```
 - Запустить redis:
```bash
redis-server
redis-cli
```
 - Запустить celery:
```bash
celery -A orders.orders worker --loglevel=info
```
 - Запустить приложение:
```bash 
python orders/manage.py runserver
```
 - Посылать запросы на сервер можно через готовую коллекцию [postman-collection](../postman_collection.json)
 - Запустить тесты:
```bash
pytest
```