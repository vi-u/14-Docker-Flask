# 14-Docker-Flask
>>>> Create Docker Flask Template

We will use Digital Ocean tutorial to make a Docker ready for installation Flask app on a proper cloud-based server.

"How To Build and Deploy a Flask Application Using Docker on Ubuntu 20.04"
https://www.digitalocean.com/community/tutorials/how-to-build-and-deploy-a-flask-application-using-docker-on-ubuntu-20-04

As a prerequisite, you need to install Docker, you may use following tutorial:

"How To Install and Use Docker on Ubuntu 20.04"
https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-20-04

>>>     Step 1 — Setting Up the Flask Application

mkdir /home/vit/Desktop/14-Docker-Flask
   
cd /home/vit/Desktop/14-Docker-Flas

mkdir -p app/static app/templates 

nano app/__init__.py
    from flask import Flask
    app = Flask(__name__)
    from app import views

nano app/views.py
    from app import app
    @app.route('/')
        def home():
        return "hello world!"

nano uwsgi.ini
    [uwsgi]
    module = main
    callable = app
    master = true

nano main.py
    from app import app
    
nano requirements.txt
    Flask>=2.0.2

Current file structure be like that:


>>>     Step 2 — Setting Up Docker






Actual file structure be like that:
