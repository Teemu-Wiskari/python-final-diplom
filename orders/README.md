### К проекту были выполнены дополнительные задачи:

 - Авторизация через соцсети
 - Тюнинг админки
 - Celery + обработка изображений (асинхронная загрузка, миниатюры)
 - Внедрение Sentry (мониторинг ошибок)
 - Кэширование с Redis (ускорение работы БД)


Запуск проекта: 

1. Создать виртуальное окружение, установить зависимости, при необходимости поменять значения в `orders/.env`
2. Создать базу данных 
```bash
createdb -U postgres diploma
```
3. Провести миграции 
```bash
python orders/manage.py migrate
```
Для silk:
```bash
python orders/manage.py collectstatic
```
4. Запустить redis
```bash
redis-server
redis-cli
```
5. Запустить celery 
```bash
celery -A orders.orders worker --loglevel=info
```
6. Запустить приложение 
```bash 
python orders/manage.py runserver
```
7. Посылать запросы на сервер можно через готовую коллекцию [postman-collection](../postman_collection.json)
8. Запустить тесты
```bash
pytest
```
9. Настройка Sentry 
   * Зарегистрируйтесь на https://sentry.io/
   * Выберите SDK для Django
   * Вставьте полученное значение DSN в .env файл
   * Перейдите по адресу http://localhost:8000/sentry-debug/
   * Проверьте трассировку ошибок Sentry в личном кабинете