![Status workflow](https://github.com/vasilevva/yamdb_final/actions/workflows/yamdb_workflow.yml/badge.svg)

# Api_yamdb
REST API проект для сервиса YaMDb — сбор отзывов о различных произведений .

### Описание 
Проект YaMDb база данных различных произведений. Произведения делятся на категории: «Книги», «Фильмы», «Музыка».
Список категорий может быть расширен. 


### Стэк технологий:
- Python
- Django Rest Framework
- Postgres
- Nginx
- Docker

### Развертывание приложения

При первом запуске на сервере необходимо проделать следующее:
- Установите docker. Инструкция по установке есть 
в [официальной документации Docker](https://docs.docker.com).
- Копировать папку *nginx* и файл *docker-compose.yaml* на сервер в домашнюю директорию.
- В домашней директории создайте файл *.env*, в котором укажите переменные окружения.
  Необходимые переменные указаны в файле *.env.example*.
- Сделайте пуш в ветку *master*, чтобы запустился workflow. 
  По его окончанию на сервере будет запущен проект.
- Далее на сервере перейдите в контейнер web:   
```sudo docker-compose exec web bash```
- Запустите миграции:  
```python manage.py migrate --noinput```
- Загрузите данные в базу данных:  
```python manage.py loaddata fixtures.json```
- Создайте пользователя:  
```python manage.py createsuperuser```
- Соберите статику:  
```python manage.py collectstatic --no-input```

Деплой на сервере при пуше в ветку *master*.
### Заполнение файла ENV
```
SECRET_KEY = ""
DB_ENGINE=django.db.backends.postgresql 
DB_NAME=postgres
POSTGRES_USER=postgres
POSTGRES_PASSWORD=postgres
DB_HOST=db
DB_PORT=5432
```
### После заупуска в dev-режиме документация доступна по адресу:
[Документация Api_yamdb](http://127.0.0.1:8000/redoc/)

### Автор
Vladimir Vasilev
Проект выполнен в ходе обучения по программе "Python-разработчик" в Яндекс.Практикум.

### License
MIT
Free Softw