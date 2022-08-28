## Начальные команды:
Запуск серверера

    python manage.py runserver # Запуск серверера

Открыть шелл режим в юпитере [настройка юпитера](pip_install.md#jupyter-django)

    python manage.py shell_plus --notebook 

## Часто используемые команды

Собрать миграции

    python manage.py makemigrations

Произвести миграции

    python manage.py migrate

Собрать все статические файлы в одном месте

    python manage.py collectstatic