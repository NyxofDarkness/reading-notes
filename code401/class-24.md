# Readings: Django REST Framework & Docker

## [Beginner’s Guide to Docker](https://wsvincent.com/beginners-guide-to-docker/)

> The entire development environment is isolated: programming language, software packages, databases, and more.

> Docker is really just Linux containers which are a type of virtualization.

> INteresting factors to think about! " What’s the downside to a virtual machine? Size and speed. A typical guest operating system can easily take up 700MB of size. So if one physical server supports three virtual machines, that’s at least 2.1GB of disk space taken up along with separate needs for CPU and memory resources."

> An image is a snapshot in time of what a project contains.

> A container is a running instance of the image.

> This is a great analogy:

- A baking analogy we can use here is as follows:

- A Dockerfile is the recipe for a cake
- An image is a snapshot of the recipe at a given time
- A docker-compose.yml says how to make the cake
- And the container is the actual, baked cake

> We can create an image and container just for Python and later add on to it.

> Steps on making an Image:

1. First create a local directory on your computer for our code.

2. Make a folding in that directory

3. make a `python3.7` folder within that folder

4. Now we need to define the image with a `Dockerfile`

``` python
 touch Dockerfile
```

5. Add the following lines of code inside the Dockerfile

``` python
# Dockerfile
FROM python:3.7-alpine
```

> Dockerfiles are read from top-to-bottom. The first instruction must be the FROM command which lets us import a base image to use for our image. This base image could be another Docker image or one we create entirely from scratch.

> using the official Docker image for Python 3.7, specifically the alpine version which includes only the bare minimum needed to run Python. The alpine version takes up 78MB of space versus full Python’s 923MB so it is a good option to start with!

> time to “build” or create the image

``` python
$ docker image build .
Sending build context to Docker daemon  2.048kB
Step 1/1 : FROM python:3.7-alpine
3.7-alpine: Pulling from library/python
c9b1b535fdd9: Pull complete
2cc5ad85d9ab: Pull complete
53a2fca3c2ea: Pull complete
30fce49de8b1: Pull complete
49bcb9571cc7: Pull complete
Digest: sha256:7655eea15dfd981eeb7d243af21e8561e967709caba938d50b136cdb992f3546
Status: Downloaded newer image for python:3.7-alpine
 ---> b2c276538711
Successfully built b2c276538711
```

> image layering: Every image is made up of one or more image layers

1. First, each image layer is immutable–unchanged–like a git commit. This helps ensure consistency when two developers build the same image. 

2. The second reason is performance. Docker caches the steps in a Dockerfile to speed up subsequent builds.

> order matters in a Dockerfile

> We’ll now create a Dockerfile for our image which will completely replace our local dev environment, so this will have Python 3 and Django. Then we’ll add a docker-compose.yml for the container instructions

> Review the similarities and differences between traditional Django and Django REST Framework.

> Django creates websites containing webpages, while Django REST Framework creates web APIs which are a collection of URL endpoints containing available HTTP verbs that return JSON.

> For django REST framework:

``` python
The second reason is performance. Docker caches the steps in a Dockerfile to speed up subsequent builds.
```

> Add it to the INSTALLED_APPS config in our settings.py file

``` python
# config/settings.py
INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',

    # 3rd party
    'rest_framework', # new

    # Local
    'books',
]
```

## [Django for APIs - Library Website](https://djangoforapis.com/library-website-and-api/)

## May ask you for email because it’s a sample chapter for (fantastic) book they’re selling

> Let’s first create a new api app.

``` python
(library) $ python manage.py startapp api
```

> Then add it to INSTALLED_APPS.

``` python
# config/settings.py
INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',

    # 3rd party
    'rest_framework',

    # Local
    'books',
    'api', # new
]
```

> . Adding an API endpoint is just like configuring a traditional Django app’s routes

> at the project-level we need to include the api app and configure its URL route, which will be api/

``` python
# config/urls.py
from django.contrib import admin
from django.urls import path, include

urlpatterns = [
    path('admin/', admin.site.urls),
    path('api/', include('api.urls')), # new
    path('', include('books.urls')),
]
```

> create a urls.py file within the api app.

``` python
(library) $ touch api/urls.py
```

> update it as follows:

``` python
# api/urls.py
from django.urls import path
from .views import BookAPIView

urlpatterns = [
    path('', BookAPIView.as_view()),
]
```

> Within our views.py file, update it to look like the following:

``` python
# api/views.py
from rest_framework import generics

from books.models import Book
from .serializers import BookSerializer


class BookAPIView(generics.ListAPIView):
    queryset = Book.objects.all()
    serializer_class = BookSerializer
```

> A serializer translates data into a format that is easy to consume over the internet, typically JSON, and is displayed at an API endpoint

> Make a serializers.py file within our api app.

``` python
(library) $ touch api/serializers.py
```

> update it as follows in a text editor

``` python
# api/serializers.py
from rest_framework import serializers

from books.models import Book


class BookSerializer(serializers.ModelSerializer):
    class Meta:
        model = Book
        fields = ('title', 'subtitle', 'author', 'isbn')
```

> we import Django REST Framework’s serializers class and the Book model from our books app. We extend Django REST Framework’s ModelSerializer into a BookSerializer class that specifies our database model Book and the database fields we wish to expose: title, subtitle, author, and isbn.

## Bookmark/Skim

-[x] [Beginner’s Guide to Django REST Framework](https://learndjango.com/tutorials/official-django-rest-framework-tutorial-beginners)
