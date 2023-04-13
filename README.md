[![Docker Compose Actions Workflow](https://github.com/Baraff24/ecommerce-backend/actions/workflows/test-docker-compose-local-dev.yml/badge.svg)](https://github.com/Baraff24/ecommerce-backend/actions/workflows/test-docker-compose-local-dev.yml)
# Django e-commerce template with docker

This is a template for a django e-commerce project with docker, django rest framework, postgresql, stripe and google oauth2.

## Technologies

- [X] Python
- [X] Django
- [X] Django Rest Framework
- [X] Docker
- [X] Postgresql

## Environments

This template is thought and designed for the docker environment. It is not recommended to use it without docker.


### How to use Docker dev

1. create a file named `.env` containing the required environment variables (read the next section)
2. run `docker-compose -f docker-compose-local-dev.yml up --build` for local dev or `docker-compose -f docker-compose-prod.yml up --build` for prod
3. work with your local files
4. execute commands inside the container. ex `docker exec -it django_template-app_1 python manage.py makemigrations`

### Features

| Features                           |                            |
|------------------------------------|:--------------------------:|
| Auto-reload                        |            ❌ No            |
| Auto migrate at start              |             ✅              |
| Auto requirements install at start |             ✅              |
| Database                           |          MariaDB           |
| Database port publicly exposed     |             ✅              |
| Reverse proxy (Nginx)              |        ⚠️ Optional         |
| Debug                              | ⚠️ Optional (default=True) |
| Admin page                         |             ✅              |
| Serving media automatically        |             ✅              |
| CORS allow all                     |  ❌ No (default=localhost)  |
| Allow all hosts                    |  ❌ No (default=localhost)  |

There is google oauth2 authentication already implemented with django-allauth.
You have to create a google oauth2 app and add the credentials to the admin page.

There is also a stripe payment system already implemented.
You have to create a stripe account and add the credentials to the .env file.

### Required environment variables

- ✅ Required
- ❌ Not required
- ⚠️ Optional

| Variables                   |     |
|-----------------------------|:---:|
| POSTGRES_PASSWORD           |  ✅  |
| SECRET_KEY                  | ⚠️  |
| EMAIL_HOST                  | ⚠️  |
| EMAIL_HOST_PASSWORD         | ⚠️  |
| EMAIL_HOST_USER             | ⚠️  |
| EMAIL_PORT                  | ⚠️  |
| DEBUG                       | ⚠️  |
| DJANGO_ALLOWED_HOSTS        |  ✅  |
| DJANGO_CORS_ALLOWED_ORIGINS |  ✅  |
| DJANGO_CSRF_TRUSTED_ORIGINS |  ✅  |

### Example .env

```
POSTGRES_PASSWORD=somerandomstring
SECRET_KEY=anotherrandomstring
EMAIL_HOST=smtp.gmail.com
EMAIL_HOST_PASSWORD=gmailpassword (Turn ON two factor authentication of gmail account, and create an app password - https://support.google.com/accounts/answer/185833)
EMAIL_HOST_USER=yourmail@gmail.com (gmail_username)
EMAIL_PORT=587
DEBUG=True
DJANGO_ALLOWED_HOSTS=*
DJANGO_CORS_ALLOWED_ORIGINS=http://localhost:5000
DJANGO_CSRF_TRUSTED_ORIGINS=http://localhost:5000
STRIPE_SECRET_KEY=sk_test_51H
STRIPE_PUBLISHABLE_KEY=pk_test_51H
```
