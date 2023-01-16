### API для проекта YaMDb

## Описание
API для работы с проектом YaMDb

## Технологии
Python 3.7 Django 2.2.16

### Как запустить проект:
- Для развёртывания проекта необходимо скачать его в нужную вам директорию, например:

 git clone git@github.com:Koloif/infra_sp2.git 

- При работе с проектом понадобится Docker настольная или консольная версия

- В директории infra создайте файл .env с переменными окружения для работы с базой данных:

DJANGO_KEY='your Django secret key'
DB_ENGINE=django.db.backends.postgresql # БД
DB_NAME=postgres # имя БД
POSTGRES_USER=postgres # логин для подключения к БД
POSTGRES_PASSWORD=postgres # пароль для подключения к БД 
DB_HOST=db # название контейнера
DB_PORT=5432 # порт для подключения к БД


- Из папки 
 infra/ 
 разверните контейнеры в новой структуре:

- Для запуска необходимо выполнить из директории с проектом команду:

 docker-compose up 

- Теперь в контейнере web нужно выполнить миграции:

 docker-compose exec web python manage.py migrate 

- Создать суперпользователя:

 docker-compose exec web python manage.py createsuperuser 

- Собрать статику:

 docker-compose exec web python manage.py collectstatic --no-input 

### Примеры запросов к API:
  1) Запрос на регистрацию:
  > _POST_ http://127.0.0.1:8000/api/v1/auth/signup/
  > 
  > Content-Type: application/json
  >
  >{
  > "username" : "user",
  > "email": "user@user.com"
  >}
     
     Ответ:
     
  >{
  > "email": "user@user.com",
  > "username": "user"
  >}
  2) Запрос на получения токена (confirmation_code получаем с указанной выше почты):
  > POST http://127.0.0.1:8000/api/v1/users/
  > 
  > Content-Type: application/json
  > 
  >{
  >  "username" : "user",
  >  "confirmation_code": "655-c68f2213fcdae8211d0f"
  >}
   
     Ответ:
     
  >{
  > "token":       "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ0b2tlbl90eXBlIjoicmVmcmVzaCIsImV4cCI6MTY2NjI5MDUzMiwianRpIjoiOTJiNDlmNWZlNzk4NDU2NmIwMjIzN2MzMDExZTU5NjgiLCJ1c2VyX2lkIjoxfQ.TWq_zyQGRmFNJhBDOCXNEtv-6fc9fEn_97vS-ZfOECE"
  >}

### А кто трудился над проектом?
 - Семёнов Кирилл https://github.com/Semyonov-K
 - Веселова Ксения https://github.com/ksuveselaya
 - Якшин Василий https://github.com/Koloif
   0
![yamdb workflow](https://github.com/koloif/yamdb_final/actions/workflows/yamdb_workflow.yml/badge.svg)
