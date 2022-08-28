# Команды Django

Все команды django-admin и manage.py [здесь](https://docs.djangoproject.com/en/4.1/ref/django-admin/)

Создать проект

    django-admin startproject project_name

Запустить сервер

    python manage.py runserver

Остановить сервер

    CTRL+C

Создать приложение

    python manage.py startapp blog

Открыть shell с jupyter

    python manage.py shell_plus --notebook

Сбор маграций

    python manage.py makemigrations

Миграции

    python manage.py migrate

Собрать статику

    python manage.py collectstatic

Создать суперюзера, он же админ

    python manage.py createsuperuser