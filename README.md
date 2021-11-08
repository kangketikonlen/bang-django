# bang-django
Ampun bang django! tet~ tet~ tet~

# Notes

## Session 1 - Creating django kickstarter
- Create local environment
```bash
python3 -m venv env
```
- Activate local environment
```bash
source env/bin/activat
```
- Upgrading pip (optional)
```bash
python -m pip install --upgrade pip
```
- Install django
```bash
python -m pip install Django
```
- Create django template
```bash
django-admin startproject app
```
## Session 2 - Urls & views
- Go to the project folder
```bash
cd app
```
- Create components
```bash
python manage.py startapp meetups
```
- Edit file called *views.py* and put code below
``` python
from django.shortcuts import render
from django.http import HttpResponse

def index(request):
    return HttpResponse("Hello World!")
```
- Create a file called *urls.py* inside the *meetups* folder
- Then, put code below
```python
from django.urls import path
from . import views

urlpatterns = [
    path("meetups/", views.index),
]
```
- Edit the *urls.py* inside the django template folder. The code should like below
```python
from django.contrib import admin
from django.urls import path, include

urlpatterns = [
    path("admin/", admin.site.urls),
    path("", include("meetups.urls")),
]
```
- Open the *settings.py* inside the django template folder and find **INSTALLED_APPS**
- Inside the lists of **INSTALLED_APPS**, put your *meetups* folder. The **INSTALLED_APPS** lists should be like below
```python
INSTALLED_APPS = [
    "django.contrib.admin",
    "django.contrib.auth",
    "django.contrib.contenttypes",
    "django.contrib.sessions",
    "django.contrib.messages",
    "django.contrib.staticfiles",
    "meetups",
]
```
- Last, run the server with
```bash
python manage.py runserver
```