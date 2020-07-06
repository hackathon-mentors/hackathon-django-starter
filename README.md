# Hackathon Django Starter

This is a quick template for starting a Django app on a Docker container with postgresql.

# Instructions

In `docker-compose.yml`, change the values of `POSTGRES_DB`, `POSTGRES_USER`, and `POSTGRES_PASSWORD`.

Run the following command to create a new app:

```shell

docker-compose run web django-admin startproject <YOUR_APP_NAME> .

```

Replace `<YOUR_APP_NAME>` with your desired app name. Don't forget the period `.` at the end, that specifies the current directory!

Once created, open `<YOUR_APP_NAME>/settings.py` file and replace the `DATABASES = ...` with the following:

```python
# settings.py

DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql',
        'NAME': 'postgres',      # Your POSTGRES_DB value
        'USER': 'postgres',      # Your POSTGRES_USER value
        'PASSWORD': 'postgres',  # Your POSTGRES_PASSWORD value     ... from docker-compose.yml
        'HOST': 'db',
        'PORT': 5432,
    }
}
```

Bring up the containers:

```shell
docker-compose up
```

Visit http://localhost:8000/ to see Django's hello world page.
