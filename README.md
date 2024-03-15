# Flask on Docker
## Overview

This project explores how to use Flask alongside Docker to make a web application. Some other components of this project consist of using Postgres to store and manage structured data, Gunicorn for running Python web applications, and Nginx for the production server. These resources were used and installed following this [tutorial published by testdriven.io](https://testdriven.io/blog/dockerizing-flask-with-postgres-gunicorn-and-nginx/). The product of the project allows one to upload media to ```http://localhost:<port>/upload```, and view them at ```http://localhost:{port}/media/{image_file_name}```. 

***Uploading and viewing an image***
![Untitled design](https://github.com/JTan242/flask-on-docker/assets/132401824/200bae48-35d7-4417-b00a-e80669ef1572)

***Build instructions***
To bring up the services follow run the following commands:

To build the images and spin the containers in the development server we can run:
```
$ docker-compose up -d --build
```
We then need to stop and remove any existing volumes and containers by running:
```
$ docker-compose down -v
```
Before proceeding to the production server, a ```.env.prod.db``` text file containing your database credentials must be included in the project root.

Now we can build the production images and spin up the containers in the production server:
```
$ docker-compose -f docker-compose.prod.yml up -d --build
$ docker-compose -f docker-compose.prod.yml exec web python manage.py create_db
```
***Notes***

a. ```docker-compose build```: builds the container

b. ```docker-compose up```: start all the services
    a. ```-d``` in deamon mode
c. ```docker-compose down```: stop all the services (equivalent to docker stop and docker rm

d. ```docker-compose exec```: run a command on an already running docker container

e. ```docker-compose run```: (probably don't want to use this for this class) brings up a container and runs a 1-off   command; useful for admin tasks

f. ```docker-compose logs [container]```: view the logs of ```container]``` or all containers if not specified
```-f``` follow mode




