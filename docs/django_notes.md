# Django Tutorial Project & Notes

[Tutorial Video Link](https://www.youtube.com/watch?v=rHux0gMZ3Eg&ab_channel=ProgrammingwithMosh)

## What is Django

- Django is a free and open-source framework for building web apps with Python
    - It is the most popular framework using framework, there are others

- Django features allows you to focus on just developing the site. All the features are optional.
    - The admin site
        - Managing the data
    - Object-relational mapper (ORM)
        - Abstracts database so can query and persist data without writing alot of SQL
    - Authentication
    - Caching

- Django has been around for a while and has a large community
    - July 2005 was when the framework was released

## How the web works

- Front end
    - Part that is loaded on the web browser on the client machine
    - Part that user sees and interacts with#

- Back end
    - Runs on web server
    - Responsible for data processing and validating business rules

- HTTP
    - Hypertext Transfer Protocol
        - For each URL that is entered
            - The client requests the information from the server
            - The server returns a response to the client
                - For example, the server might return a generated page as a HTML page to the server
                - Alternatively, the server might just return the data to the client, and the client is responsible on generating the page

- It is now considered industry best practice for the server to return data, and the client genereates the page
    - As it is more scalable, less responsibility on the server
    - The server becomes a gateway to the data
        - Server provides endpoints the client can request information from
    - The server acts as an interface to all these endpoints
        - The server provides an API (Application Programming Interface)

## Creating your first Django project

- In terminal
    - mkdir storefront
    - cd storefront
    - pipenv install django
        - installing django inside a virtual environment
    - pipenv shell
        - activates virutal environment
    - django-admin
        - utility that comes with django
    - python manage.py runserver

- Generated files
    - __init__.py
        - defines directory as a package
    - settings.py
        - application settings
    - urls.py
        - URLs within the application
    - manage.py
        - Takes settings of projects
        - Wrapper around django-admin
            - python manage.py runserver
            - uses port 8000 by default, but can specify port number

- Django projects is essentially a collection apps providing different functionality

settings.py contains the list default INSTALLED_APPS
```python
INSTALLED_APPS = [
    'django.contrib.admin', # admin interface for managing data
    'django.contrib.auth', # used for authenticating users
    'django.contrib.contenttypes',
    'django.contrib.sessions', # legacy, not used anymore - temp server for managing user data
    'django.contrib.messages', # displaying one time notifications to users
    'django.contrib.staticfiles', # used for serving static data
]
```

- You can create your app through `python manage.py startapp {{ name of app }}`
    - Every django has the same structure
        - admin.py is where admin interface is define for the app
        - apps.py is a misleading name but is where config for the app is set
        - models.py is where the where model classes are defined (pulling data from databases to present to user)
        - tests.py is where unit tests live
        - views.py is essentially the requests handler

- Need to update created apps in the django projects settings.py INSTALLED_APPS list

## Writing views

- HTTP is a request response protocol
    - We do this through views in django
    - Django view functions take a request and return a response
        - The function is essentially a request handler
        - In some frameworks, it's called an action
            - In django it's known as a view (confusing ik)

## Data Modelling

- When app boundaries are too large
    - end up with monolithic structure which is hard to use

- When app boundaries are too small
    - end up with highly coupled structure

- Good design
    - Minimal coupling
    - High cohesion
        - Each app does one thing and does it well
        - Apps are well focussed