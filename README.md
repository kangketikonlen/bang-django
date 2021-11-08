# bang-django
Ampun bang django! tet~ tet~ tet~

# Notes

## Session 1 - Creating django kickstarter
- Create local environment **python3 -m venv env**
- Activate local environment **source env/bin/activate**
- Upgrading pip (optional) **python -m pip install --upgrade pip**
- Install django **python -m pip install Django**
- Create django template **django-admin startproject *name_without_dash_or_space***

## Session 2 - Urls & views
- Go to the project folder **cd *name_without_dash_or_space***
- Create components **python manage.py startapp *component_name***
- Edit file called *views.py* and put code below
``` python
from django.shortcuts import render
from django.http import HttpResponse

def index(request):
    return HttpResponse("Hello World!")
```
- Create a file called *urls.py* inside the *components* folder
- Then, put code below
```python
from django.urls import path
from . import views

urlpatterns = [
    path("component_name/", views.index),
]
```
- Edit the *urls.py* inside the django template folder. The code should like below
```python
from django.contrib import admin
from django.urls import path, include

urlpatterns = [
    path("admin/", admin.site.urls),
    path("", include("component_name.urls")),
]
```
- Open the *settings.py* inside the django template folder and find **INSTALLED_APPS**
- Inside the lists of **INSTALLED_APPS**, put your *component_name* folder. The **INSTALLED_APPS** lists should be like below
```python
INSTALLED_APPS = [
    "django.contrib.admin",
    "django.contrib.auth",
    "django.contrib.contenttypes",
    "django.contrib.sessions",
    "django.contrib.messages",
    "django.contrib.staticfiles",
    "component_name",
]
```
- Last, run the server with **python manage.py runserver**