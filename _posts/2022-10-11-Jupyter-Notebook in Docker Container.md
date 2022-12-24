---
author: piragenth
categories:
- Docker
date: "2022-11-27"
tags:
- Docker
- How-TO
- Linux
title: Jupyter-Notebook in Docker Container | Jupyter notebook Docker
---

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


# Running Jupyter Container

creating jupyter notebook container is very easy 
do like shown bellow

```bash 
Docker run -d -p 8888:8888 jupyter/minimal-notebook
```

This is the simple way to bring jupyter notebook container up.

If you want to use jupyter notebook **without a password** just add this at the end "```
--ip='*' --NotebookApp.token='' --NotebookApp.password=''" 
```bash 
docker run -d -p 80:80 jupyter/minimal-notebook -v {mount direcory in host}:/home/jovyan/ --ip='*' --NotebookApp.token=''  --NotebookApp.password='' --port=80
```
make sure to use the same port inside container and the host.

## Jupyter Lab

type **http://localhost:8888/lab** for jupyter Lab

![](https://linuxtutorialforbeginners.com/assets/Pictures/jupyter-lab.png)

## Jupyter Notebook

type **http://localhost:8888/notebook** for jupyter Notebook
![](https://linuxtutorialforbeginners.com/assets/Pictures/jupyter-notebook.png)
