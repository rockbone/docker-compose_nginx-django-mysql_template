# Description

Setup Nginx+Django+uWSGI+MySQL for development purpose with docker-compose.

# USAGE

    # create django project
    docker-compose run python django-admin.py startproject mysite .

    # create app
    docker-compose run python python manage.py startapp app

    # add settings.py
        # to use mysql
        import pymysql
        pymysql.install_as_MySQLdb()
        DATABASES = {
            'default': {
                'ENGINE': 'django.db.backends.mysql',
                'NAME': 'app',
                'USER': 'app',
                'PASSWORD': 'app',
                'HOST': 'db',
                'PORT': '3306',
            }
        }
        # specify static directory
        STATIC_ROOT = '/static'

    # migrate database
    docker-compose run python ./manage.py makemigrations
    docker-compose run python ./manage.py migrate

    # collect static
    docker-compose run python ./manage.py collectstatic

    # create superuser
    docker-compose run python ./manage.py createsuperuser

    # boot up docker
    docker-compose up -d

    # check site
    http://localhost:8000/admin
