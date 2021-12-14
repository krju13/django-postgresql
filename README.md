# django-postgresql

this is on the [https://docs.docker.com/samples/django/](https://docs.docker.com/samples/django/)

if you use wsl2
then change the docker-compose.yml like this
```
version: "3.9"

services:
  db:
    image: postgres:13.3-buster
    user: ${POSTGRES_UID}:${POSTGRES_GID}
    volumes:
      - postgres-vol:/var/lib/postgresql/data:z
    restart: always
    ports:
      - "5432"
    environment:
      - POSTGRES_DB=postgres
      - POSTGRES_USER=postgres
      - POSTGRES_PASSWORD=postgres
  web:
    build: .
    command: python manage.py runserver 0.0.0.0:8000
    volumes:
      - .:/code
    ports:
      - "8000:8000"
    depends_on:
      - db
volumes:
  postgres-vol:
```
then error will fix.