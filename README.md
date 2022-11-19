# 14-Docker-Flask
>>>> Create Docker Flask Template

We will use Digital Ocean tutorial to make a Docker ready for installation Flask app on a proper cloud-based server.

"How To Build and Deploy a Flask Application Using Docker on Ubuntu 20.04"
https://www.digitalocean.com/community/tutorials/how-to-build-and-deploy-a-flask-application-using-docker-on-ubuntu-20-04

As a prerequisite, you need to install Docker, you may use following tutorial:

"How To Install and Use Docker on Ubuntu 20.04"
https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-20-04

>>>     Step 1 — Setting Up the Flask Application

    sudo mkdir 14-Docker-Flask
   
    sudo cd 14-Docker-Flas

    sudo mkdir -p app/static app/templates 

    sudo nano app/__init__.py
#which contains

    from flask import Flask
    app = Flask(__name__)
    from app import views

#   
    sudo nano app/views.py
#which contains

    from app import app
    @app.route('/')
        def home():
        return "hello world!"

#
    sudo nano uwsgi.ini

which contains

    [uwsgi]
    module = main
    callable = app
    master = true

#
    sudo nano main.py
#which contains

    from app import app
#    
    sudo nano requirements.txt
#which contains

    Flask>=2.0.2



>>>     Step 2 — Setting Up Docker

    sudo nano Dockerfile
#which contains

    FROM tiangolo/uwsgi-nginx-flask:python3.8-alpine
    RUN apk --update add bash nano
    ENV STATIC_URL /static
    ENV STATIC_PATH /var/www/app/static
    COPY ./requirements.txt /var/www/requirements.txt
    RUN pip install -r /var/www/requirements.txt

#To check if port 56733 is open run this command on server, it needs to be >1

    sudo nc localhost 56733 < /dev/null; echo $? 

#a shell script that will build an image from the Dockerfile and create a container

    sudo nano start.sh                            
#which contains

    #!/bin/bash
    app="docker.test"
    docker build -t ${app} .
    docker run -d -p 56733:80 \
      --name=${app} \
      -v $PWD:/app ${app}

#Execute the script to create the Docker image and build a container

    sudo bash start.sh       

#Check if it is open and running

    sudo docker ps

#To verify if it is running in a browser type http://localhost:56733

    http://ip-address:56733   

*******

Current file structure is as follows:
https://github.com/vi-u/14-Docker-Flask/blob/main/docker_flask_structure.txt





