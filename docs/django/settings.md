# Файл настроек

Здесь будет описано все что мы добавим в settings или изменим стандартные настройки

Полное описание стандартных настроек можно найти здесь: [https://docs.djangoproject.com/en/4.1/ref/settings/](https://docs.djangoproject.com/en/4.1/ref/settings/)

### Настроки для jupyter

```python
INSTALLED_APPS = [
    # ...
    'django_extensions',
    # ...
]

os.environ["DJANGO_ALLOW_ASYNC_UNSAFE"] = "true" # убрать в продакшене!!!
```

### Добавление своего приложения

```python
INSTALLED_APPS = [
    # ...
    'blog',
]
```

### Настройки Django Debug Toolbar
```python
# settings.py
INSTALLED_APPS = [
    # ...
    "debug_toolbar", # удалить в продакшене
    # ...
]

# ....

MIDDLEWARE = [
    # ...
    "debug_toolbar.middleware.DebugToolbarMiddleware", # удалить в продакшене
    # ...
]

# ....

INTERNAL_IPS = [
    # ...
    "127.0.0.1", # удалить в продакшене
    # ...
]
```

Файл urls.py
```python
# urls.py
from django.urls import include, path

urlpatterns = [
    # ...
    path('__debug__/', include('debug_toolbar.urls')), # удалить в продакшене
]
```