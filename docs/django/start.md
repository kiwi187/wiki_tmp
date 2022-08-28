## Создание проекта

Активируем виртуальное окружение `venv\Scripts\activate` [подробнее здесь](/pip_install#_1)

Создать проект [документация](https://docs.djangoproject.com/en/4.1/intro/tutorial01/)

    django-admin startproject project_name

Появится начальная структура проекта:

    project_name/
        manage.py
        project_name/
            __init__.py
            settings.py
            urls.py
            asgi.py
            wsgi.py

После этого можно проверить правильно ли все сделали.

Запускаем проект

    python manage.py runserver

В консоли увидим сообщение что сервер запущен

Переходим по ссылке [http://127.0.0.1:8000/](http://127.0.0.1:8000/) и если видим ракету и поздравления то все гуд. Можно ехать дальше

## Создание приложения

Остановим сервер. В консоли нажимаем `Ctrl + C`

Создаем приложение:

    python manage.py startapp blog

В корне добавится папка blog со структурой

    blog/
        __init__.py
        admin.py
        apps.py
        migrations/
            __init__.py
        models.py
        tests.py
        views.py

Добавим приложение в [settings](settings.md)

```python
INSTALLED_APPS = [
    ........
    'blog',
]
```