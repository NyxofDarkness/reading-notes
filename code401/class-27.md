# Readings: API Deployment

## [Django Settings Best Practices](https://djangostars.com/blog/configuring-django-settings-best-practices/)

> Managing Django Settings: Issues

1. Different environments: You need an approach that allows you to keep all these Django setting configurations.

2. Sensitive data: You have SECRET_KEY in each Django project. On top of this there can be DB passwords and tokens for third-party APIs, you need to store these safely

3. Sharing settings between team members: general approach to eliminate human error when working with the settings.

4. Django settings are a Python code: instead of key-value pairs, settings.py can have a very tricky logic.

> Setting Configuration: Different Approaches

> There is no built-in universal way to configure Django settings. Here are some popular ones!

> settings_local.py: The basic idea of this method is to extend all environment-specific settings in the settings_local.py file

``` python

ALLOWED_HOSTS = ['example.com']
DEBUG = False
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql',
        'NAME': 'production_db',
        'USER': 'user',
        'PASSWORD': 'password',
        'HOST': 'db.example.com',
        'PORT': '5432',
        'OPTIONS': {
            'sslmode': 'require'
        }
    }
}

...

from .settings_local import *
```

> settings_local.py file:

``` python
ALLOWED_HOSTS = ['localhost']
DEBUG = True
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql',
        'NAME': 'local_db',
        'HOST': '127.0.0.1',
        'PORT': '5432',
    }
}
```

> Pros:
Secrets not in VCS.

> Cons:
settings_local.py is not in VCS, so you can lose some of your Django environment settings.
The Django settings file is a Python code, so settings_local.py can have some non-obvious logic.
You need to have settings_local.example (in VCS) to share the default configurations for developers

> Separate settings file for each environment: allows you to keep all configurations in VCS and to share default settings between developers.

>  make a settings package with the following file structure:

``` python
settings/
   ├── __init__.py
   ├── base.py
   ├── ci.py
   ├── local.py
   ├── staging.py
   ├── production.py
   └── qa.py

#settings/local.py
from .base import *


ALLOWED_HOSTS = ['localhost']
DEBUG = True
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql',
        'NAME': 'local_db',
        'HOST': '127.0.0.1',
        'PORT': '5432',
    }
}
# To run a project with a specific configuration, you need to set an additional parameter:

python manage.py runserver --settings=settings.local
```

> Pros:
All environments are in VCS.
It’s easy to share settings between developers.

> Cons:
You need to find a way to handle secret passwords and tokens.
“Inheritance” of settings can be hard to trace and maintain.

> Environment variables:  solve the issue with sensitive data

``` python

import os


SECRET_KEY = os.environ['SECRET_KEY']
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql',
        'NAME': os.environ['DATABASE_NAME'],
        'HOST': os.environ['DATABASE_HOST'],
        'PORT': int(os.environ['DATABASE_PORT']),
    }
}
```

> Pros:
Configuration is separated from code.
Environment parity – you have the same code for all environments.
No inheritance in settings, and cleaner and more consistent code.
There is a theoretical grounding for using environment variables – 12 Factors.

> Cons:
You need to handle sharing default config between developers.

> 12 Factors is a collection of recommendations on how to build distributed web-apps that will be easy to deploy and scale in the Cloud.  **heroku**

> the collection consists of twelve parts:

1. Codebase

2. Dependencies

3. Config

4. Backing services

5. Build, release, run

6. Processes

7. Port binding

8. Concurrency

9. Disposability

10. Dev/prod parity

11. Logs

12. Admin processes

> Each point describes a recommended way to implement a specific aspect of the project

> django-environ: environment variables are the perfect place to store settings.

> This app gives a well-functioning API for reading values from environment variables or text files, handful type conversion, etc.

``` python
# settings.py
import environ


root = environ.Path(__file__) - 3  # get root of the project
env = environ.Env()
environ.Env.read_env()  # reading .env file

SITE_ROOT = root()

DEBUG = env.bool('DEBUG', default=False)
TEMPLATE_DEBUG = DEBUG

DATABASES = {'default': env.db('DATABASE_URL')}

public_root = root.path('public/')
MEDIA_ROOT = public_root('media')
MEDIA_URL = env.str('MEDIA_URL', default='media/')
STATIC_ROOT = public_root('static')
STATIC_URL = env.str('STATIC_URL', default='static/')

SECRET_KEY = env.str('SECRET_KEY')

CACHES = {'default': env.cache('REDIS_CACHE_URL')}

# .env file
DEBUG=True
DATABASE_URL=postgres://user:password@db.example.com:5432/production_db?sslmode=require
REDIS_CACHE_URL=redis://user:password@cache.example.com:6379/1
SECRET_KEY=Some-Autogenerated-Secret-Key
```

> Instead of splitting settings by environments, you can split them by the source: Django, third- party apps (Celery, DRF, etc.), and your custom settings.

> file structure

``` python
project/
├── apps/
├── settings/
│   ├── __init__.py
│   ├── djano.py
│   ├── project.py
│   └── third_party.py
└── manage.py

# __init.py file

from .django import *       # All Django related settings
from .third_party import *  # Celery, Django REST Framework & other 3rd parties
from .project import *      # You custom settings

# Each module could be done as a package

project/
├── apps/
├── settings/
│   ├── project
│   │   ├── __init__.py
│   │   ├── custom_module_foo.py
│   │   ├── custom_module_bar.py
│   │   └── custom_module_xyz.py
│   ├── third_party
│   │   ├── __init__.py
│   │   ├── celery.py
│   │   ├── email.py
│   │   └── rest_framework.py
│   ├── __init__.py
│   └── djano.py
└── manage.py
```

> Django Settings: Best practices

1. Keep settings in environment variables.

2. Write default values for production configuration (excluding secret keys and tokens).

3. Don’t hardcode sensitive settings, and don’t put them in VCS.

4. Split settings into groups: Django, third-party, project.

5. Follow naming conventions for custom (project) settings.

## [SSH Tutorial](https://www.hostinger.com/tutorials/ssh-tutorial-how-does-ssh-work)

## Bookmark/skim

-[x] [ White Noise](http://whitenoise.evans.io/en/stable/)

-[x] [ IaaS](https://en.wikipedia.org/wiki/Infrastructure_as_a_service)

-[x] [PaaS](https://en.wikipedia.org/wiki/Platform_as_a_service)

-[x] [CORS](https://en.m.wikipedia.org/wiki/Cross-origin_resource_sharing)