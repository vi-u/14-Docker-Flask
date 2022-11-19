# 14-Docker-Flask
>>>> Create Docker Flask Template

We will use Digital Ocean tutorial to make a Docker ready for installation Flask app on a proper cloud-based server.

"How To Build and Deploy a Flask Application Using Docker on Ubuntu 20.04"
https://www.digitalocean.com/community/tutorials/how-to-build-and-deploy-a-flask-application-using-docker-on-ubuntu-20-04

As a prerequisite, you need to install Docker, you may use following tutorial:

"How To Install and Use Docker on Ubuntu 20.04"
https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-20-04

Actual file structure be like that:

14-Docker-Flask        #home/vit/Desktop/14-Docker-Flask
|
|---app
|   |---static
|   |   |---           #None yet
|   |
|   |---templates
|   |   |---home.html  #Holds web pages, forms, outputs
|   |
|   |---__init__.py    #Creates Flask Instance
|   |
|   |---views.py       #Contains most of app logic
|
|
|---uwsgi.ini          #Contains Server configuration
| 
|---main.py            #Was configured by uwsgi.ini
|
|---requirements.txt  

