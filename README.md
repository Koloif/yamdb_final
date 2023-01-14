### API для проекта YaMDb

## Описание
API для работы с проектом YaMDb

## Технологии
Python 3.7 Django 2.2.16

### Как запустить проект:
Клонировать репозиторий и перейти в него в командной строке:

```
git clone https://github.com/Koloif/api_yamdb.git
```
```
cd api_yamdb
```
Cоздать и активировать виртуальное окружение:

```
python3 -m venv venv
```

```
source venv/scripts/activate
```

```
python3 -m pip install --upgrade pip
```

Установить зависимости из файла requirements.txt:

```
pip install -r requirements.txt
```

Выполнить миграции:

```
python3 manage.py migrate
```

Запустить проект:

```
python3 manage.py runserver
```
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

### А кто трудился над  проектом?
 - Семёнов Кирилл https://github.com/Semyonov-K
 - Веселова Ксения https://github.com/ksuveselaya
 - Якшин Василий https://github.com/Koloif
