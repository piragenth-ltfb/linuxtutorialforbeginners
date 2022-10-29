---
layout: post
title: How to Deploy phpMyAdmin in Docker
date: '2022-10-29'
#images: [https://ddewaele.github.io/assets/images/jekyll_docker/logo.png]   
categories: [Docker,jekyll]
tags: [Docker, How-TO, jekyll, Linux]
author: piragenth
---
![](/assets/Pictures/0-containerize-mysql-and-phpmyadmin-using-docker-containers-banner.jpg)

> Requirements
#### * Install docker 
```bash
sudo apt install docker.io -y
```

> Create Docker Network (optional)

```bash
docker network create {network-name}
```

> Creating Docker Container

to create a file
```bash
nano docker-phpmyadmin.yaml
```
add content bellow to the file

```yaml
version: '3.1'

services:
  phpmyadmin:
    container_name: phpmyadmin
    image: phpmyadmin
    restart: always
    ports:
      - 8080:80
    environment:
      - PMA_HOST=mysql
      - PMA_ARBITRARY=1
    depends_on:
      - mysql
  
    db:
      image: mysql:latest
      container_name: mysql
      restart: always
      ports:
        - 3306:3306
      environment:
      MYSQL_ROOT_PASSWORD: <password for mysql>
```

```bash
docker-compose -f docker-phpmyadmin.yaml up 
```

> Access phpmyadmin


To get the docker network gateway ip:

```bash
docker inspect phpmyadmin
```

In the output you will find gateway under 'gateway:'

![](/assets/Pictures/docker-networks-gateway.png)




Go to the browser to access phyMyAdmin: http://localhost:8080/

The default user is 'root' and the password will the password set on docker-phpmyadmin.yaml

Because we are using phpmyadmin in docker we can't use 'localhost'. So in this case we are going to use docker network's gateway ip

![](/assets/Pictures/Phpmyadmin.png)

