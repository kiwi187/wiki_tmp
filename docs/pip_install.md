## Виртуальное окружение

Для начала создается виртуальное окружение

    cd any_folder
    python -m venv venv

Запуск вирт окружения (Windows)

    venv\Scripts\activate #Находясь в папке с папкой venv

## Установка Django

Установка последней версии django ([Оф доки](https://docs.djangoproject.com/en/4.1/topics/install/#installing-official-release]))

    python -m pip install Django

Установка конкретной версии Django (Для продакшн версии лучше выбирать LTE релиз) [посмотреть версии django](https://www.djangoproject.com/download/)

    pip install Django==3.2



## Установка и настройка jupyter для django 

Установка пакета ([Оф. Доки](https://jupyter.org/install))

    pip install notebook 

Так же понадобится бибилиотека django_extensions ([Оф. Доки](https://django-extensions.readthedocs.io/en/latest/installation_instructions.html#installing))

    pip install django-extensions

В settings.py довабить приложение:

```python
INSTALLED_APPS = [
    # ...
    'django_extensions',
    # ...
]

os.environ["DJANGO_ALLOW_ASYNC_UNSAFE"] = "true" # убрать в продакшене!!!
```

Запуск

    python manage.py shell_plus --notebook

## Установка Django Debug Toolbar

Ссылка на оф документацию: [https://django-debug-toolbar.readthedocs.io/en/latest/installation.html](https://django-debug-toolbar.readthedocs.io/en/latest/installation.html)

    python -m pip install django-debug-toolbar

Обязательное наличие следующих настроек (могут быть в разных места файла... Поискать!):
```python
# settings.py
INSTALLED_APPS = [
    # ...
    "django.contrib.staticfiles",
    # ...
]

STATIC_URL = "static/"

TEMPLATES = [
    {
        "BACKEND": "django.template.backends.django.DjangoTemplates",
        "APP_DIRS": True,
        # ...
    }
]
```

Добавить приложение и внести необходимые настройки
```python
# settings.py
INSTALLED_APPS = [
    # ...
    "debug_toolbar", # удалить в продакшене
    # ...
]
```
```python
# settings.py
MIDDLEWARE = [
    # ...
    "debug_toolbar.middleware.DebugToolbarMiddleware", # удалить в продакшене
    # ...
]
```
```python
# settings.py

INTERNAL_IPS = [
    # ...
    "127.0.0.1", # удалить в продакшене
    # ...
]
```

Добавьте URL-адреса
```python
# urls.py
from django.urls import include, path

urlpatterns = [
    # ...
    path('__debug__/', include('debug_toolbar.urls')), # удалить в продакшене
]
```

## django-crispy-forms

Документация: [https://django-crispy-forms.readthedocs.io/en/latest/index.html](https://django-crispy-forms.readthedocs.io/en/latest/index.html)

    pip install django-crispy-forms

добавить в файл настроек

```python
# settings.py
# ...
INSTALLED_APPS = (
    ...
    'crispy_forms',
)
# ...
CRISPY_TEMPLATE_PACK = 'uni_form'
```

## python-dotenv

Документация: [https://pypi.org/project/python-dotenv/](https://pypi.org/project/python-dotenv/)

    pip install python-dotenv

Настройки:

```python
# settings.py
from dotenv import load_dotenv

# Loading ENV
env_path = Path('.') / '.env'
load_dotenv(dotenv_path=env_path)

SECRET_KEY = os.getenv('SECRET_KEY')
```

## django-ckeditor

Документация [https://django-ckeditor.readthedocs.io/en/latest/](https://django-ckeditor.readthedocs.io/en/latest/)

    pip install django-ckeditor

Настройки:

```python
# settings.py
INSTALLED_APPS = [
    # ...
    'ckeditor',
 ] 


CKEDITOR_CONFIGS = {
    'default': {
        'width':'auto',
    },
}
```