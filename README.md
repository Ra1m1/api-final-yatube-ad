# Yatube API

REST API для социальной сети Yatube, где пользователи могут публиковать посты, комментировать их, подписываться друг на друга и объединяться в сообщества.

## Технологии

- Python 3.9
- Django 3.2
- Django REST Framework
- Simple JWT

## Установка

1. Клонировать репозиторий:
```bash
   git clone https://github.com/Ra1m1/api_final_yatube.git
   cd api_final_yatube/yatube_api
```

2. Создать и активировать виртуальное окружение:
```bash
   python -m venv venv
   source venv/bin/activate  # Linux/Mac
   venv\Scripts\activate     # Windows
```

3. Установить зависимости:
```bash
   pip install -r requirements.txt
```

4. Выполнить миграции:
```bash
   python manage.py migrate
```

5. Запустить сервер:
```bash
   python manage.py runserver
```

## Аутентификация

API использует JWT-токены. Получить токен:

POST /api/v1/jwt/create/ { "username": "your_username", "password": "your_password" }

## Примеры запросов

### Получить список постов

GET /api/v1/posts/

### Создать пост (требует авторизации)

POST /api/v1/posts/ Авторизация: Bearer <токен> { "text": "Текст публикации", "group": 1 }

### Получить комментарии к посту

GET /api/v1/posts/{post_id}/comments/

### Подписаться на пользователя

POST /api/v1/follow/ Authorization: Bearer <токен> { "following": "username" }

### Получить свои подписки (с поиском)

GET /api/v1/follow/?search=username Authorization: Bearer <токен>
