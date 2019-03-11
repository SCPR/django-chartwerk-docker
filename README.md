Chartwerk on Docker
===================

Structure
---------

The application is deployed as a series of services, which should run seamlessly on a local machine (in my case a Mac using OSX) and can be deployed to Amazon ECS with some additional configuration.

  - Nginx
  - PostgreSQL
  - Redis (for the Celery queue)
  - A Django-ready web application server

The local configuration will spin up a Postgres container, but in production you may want to use a persistent database like an RDS instance. You should add your database settings as environment variables, which by default live in `config/env`. Just be careful not to check those into Github.

Dependencies
------------

The nice thing about deploying this app via Docker is that the only dependency should be Docker itself. You'll also want an AWS account and a couple utilities if you want to deploy this to the Internet.

Installation instructions for Docker and its associated utilities can be found [here](https://docs.docker.com/docker-for-mac/).

Quickstart
----------

Once you have installed Docker and docker-compose, running the app locally is easy:

```
git clone https://github.com/SCPR/docker-admin-chartwerk.git
cd docker-admin-chartwerk
docker-compose build
docker-compose up
```

Then just visit `127.0.0.1:8000/chartwerk` and it should be running. The app will then prompt you to login in. The default username and password are both **admin**.
