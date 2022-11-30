---
title: "How to Deploy Flask and MySQL in Docker"
date: 2022-11-22T08:11:49+05:30
draft: false
tag:
  - Docker
  - How-To
---


In this tutorial we will go through an example of taking an existing simple web app based on Flask and MySQL and making it run with Docker and docker-compose

So we are going to create two container on for Flask it self and mysql container

<hr>

## Prerequisite

* Docker 
```bash 
# Debian based distro 
sudo apt install docker.io -y


```

* docker-compose

```bash
#debian based distro 
sudo apt install docker-compose -y

```

<hr>

## Setting up project

For an reference this is how my flask project folder look like

```
bash
# flask project structure
.
├── app.py
├── docker-flask.yaml
├── flask-app.sh
├── requirements.txt
└── templates
    ├── adduser.html
    ├── edit.html
    └── index.html

```
create requirement.txt 

```bash
pip freeze > requirement.txt
```
this will output the required pip dependencies list
 

## Creating Docker image 

We want to create an docker image for flask app

```bash
# Use an official Python runtime as an image
FROM python:3.6

# The EXPOSE instruction indicates the ports on which a container 
# will listen for connections
# Since Flask apps listen to port 5000  by default, we expose it
EXPOSE 5000

# Sets the working directory for following COPY and CMD instructions
# Notice we haven’t created a directory by this name - this instruction 
# creates a directory with this name if it doesn’t exist
WORKDIR /app

# Install any needed packages specified in requirements.txt
COPY requirements.txt /app
RUN pip install -r requirements.txt

# Run app.py when the container launches
COPY app.py /app
CMD python app.py
```


What this does is simply as described in the file — base the image on a Python 3.6 image, expose port 5000 (for Flask), create a working directory to which requirements.txt and app.py will be copied, install the needed packages and run the app.


## Creating docker-compose.yml

Create new docker-compose.yaml file

```yaml
version: '3'
services:
  flask:
    image: piragenthdocker/flask:ubuntu
    container_name: flask
    restart: always
    ports:
      - 80:80
    volumes:
      - .:/home/Flask
    command: bash /home/Flask/flask-app.sh
    depends_on:
      - mysql
    networks:
      - docker-compose_default

  mysql:
    image: mysql:latest
    container_name: mysql
    restart: always
    networks:
      - docker-compose_default
    ports:
      - 3306:3306
    environment:
      MYSQL_ROOT_PASSWORD: <Mysql PASSWORD>

networks:
  docker-compose_default:
    external: true
```
create new flask-app.sh file 

```bash
#!/bin/bash

echo 'nameserver 8.8.8.8' > /etc/resolv.conf
pip3 install -r requirements.txt
python3 app.py 

```

inside app.py 

this is a referance 

```python
from flask import Flask, render_template, url_for, redirect, request, flash
from flask_mysqldb import MySQL

app = Flask(__name__)

#Mysql connection
app.config['MYSQL_HOST']='172.18.0.1'
app.config['MYSQL_PORT']=3306
app.config['MYSQL_USER']='root'
app.config['MYSQL_PASSWORD']='mysql PASSWORD'
app.config['MYSQL_DB']='db_naem'
app.config['MYSQL_CURSORCLASS']='DictCursor'
mysql = MySQL(app)

```


## Running the app


in order to run the out dockerized app, we will execute the following command from the terminal 

```bash
docker-compose up 
```

