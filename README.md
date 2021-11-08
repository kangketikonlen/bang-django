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
## Session 3 - Getting Started with Templates
- Create a folder called *templates* inside the *meetups* or component that we create before.
- Then create *index.html* file inside *templates* folder.
- Edit *index.html* that we created before. You can be creative or follow the code below
```html
<!DOCTYPE html>
<html lang="en">

<head>
	<meta charset="UTF-8">
	<meta http-equiv="X-UA-Compatible" content="IE=edge">
	<meta name="viewport" content="width=device-width, initial-scale=1.0">
	<title>All Meetups</title>
</head>

<body>
	<h1>All Meetups</h1>
	<p>Hello World!</p>
</body>

</html>
```
- Edit the *views.py* inside the *meetups* folder, then change the code as below
```python
from django.shortcuts import render

def index(request):
    return render(request, "index.html")
```
## Session 4 - Static Files & First Steps with Django Template Lang
- Create a folder called *static* inside *meetups* component folder
- Create 3 folders called *images*, *scripts* and *styles*
- Create css file called *base.css* inside *styles* folder. You can be creative or follow this css rules
```css
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&family=Roboto+Slab:wght@700&display=swap');
* {
	box-sizing: border-box;
}

body {
	font-family: 'Roboto', sans-serif;
	margin: 0;
	background-color: #ccc3db;
	color: #3e3e41;
}

h1, h2, h3 {
	font-family: 'Roboto Slab', sans-serif;
	color: #222224;
}

button, .btn {
	cursor: pointer;
	font: inherit;
	padding: 0.5rem 1.5rem;
	background-color: #350490;
	border: 1px solid #350490;
	color: white;
	border-radius: 4px;
	text-decoration: none;
}

button:hover, .btn:hover {
	background-color: #230161;
	border-color: #230161;
}

#main-header {
	width: 100%;
	text-align: center;
	padding: 2rem 0;
}

#main-header h1 {
	font-size: 1.5rem;
}

#main-logo {
	font-size: 3rem;
	font-family: 'Roboto Slab', sans-serif;
	text-decoration: none;
	color: #350490;
	font-weight: bold;
}
```
- Edit *index.html* file inside the *templates* folder and change the code as below
```html
{% load static %}
<!DOCTYPE html>
<html lang="en">

<head>
	<meta charset="UTF-8">
	<meta http-equiv="X-UA-Compatible" content="IE=edge">
	<meta name="viewport" content="width=device-width, initial-scale=1.0">
	<title>All Meetups</title>
	<link rel="stylesheet" href="{% static 'meetups/styles/base.css' %}">
</head>

<body>
	<h1>All Meetups</h1>
	<p>Hello World!</p>
</body>

</html>
```