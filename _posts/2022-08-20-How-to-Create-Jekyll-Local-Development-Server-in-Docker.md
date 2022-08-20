---
layout: post
title: How to Create Jekyll Local Development Server in Docker
date: '2022-08-20'
categories: [Docker,jekyll]
author: piragenth
---

## What is Jekyll
Jekyll is a [static site generator.](https://www.cloudflare.com/learning/performance/static-site-generator/#:~:text=A%20static%20site%20generator%20is,to%20users%20ahead%20of%20time.){:target='blank'}((SSC).It takes text written in your favorite markup language and uses layouts to create a static website. You can tweak the site’s look and feel, URLs, the data displayed on the page, and more.

## Installing docker
#### Updating repo 
```bash
sudo apt update 
```
```bash 
sudo apt install docker.io
```
Installing docker-compose

```bash 
sudo apt install docker-compose
```
## Cloning jekyll theme

Jekyll has an extensive theme system that allows you to leverage community-maintained templates and styles to customize your site's presentation. Jekyll themes specify plugins and package up assets, layouts, includes, and stylesheets in a way that can be overridden by your site's content.

I personally use [jekyll-theme-chripy](https://github.com/cotes2020/jekyll-theme-chripy){:target='blank'} in my website. So i am going use this theme as an example in tutorial.you can choose whatever theme you like.[themes.jekyll.]

### Pick up a theme

* [https://jamstackthemes.dev](jamstackthemes.dev){:target='blank'}
* [https://jekyllthemes.org](jekllthemes.org){:target='blank'}
* [https://jekyllthemes.io](jekyllthemes.io){:target='blanka'}
* [https://jekyll-themes.com](jekyll-themes.com){:target='blank'}

### optional : forking theme

i recommend you to fork you repo. So after your development you can host your jekyll website for free in [Github-Pages](https://pages.github.com/){:target='blank'}, [Netlify](https://www.netlify.com/){:target='blank'}
[how to fork github repo](https://blog.devgenius.io/how-to-fork-a-repository-and-push-and-pull-with-github-48b296b2b623){:target='blank'}



## Deploying jekyll in docker

Create docker-compose file 
```bash 
nano docker-compose.yaml
```
this will open a CLI based test editor and add this yaml file 

```yaml
version: '3'
services:
  jekyll-serve:
    container_name: jekyll
    image: jekyll/jekyll:latest
    volumes:
      - "{Jekyll theme root folder}:/srv/jekyll"
    ports:
      - 80:4000
    command: 'jekyll serve'
    restart: unless-stopped
```

running docker-compose

```bash 
docker-compose up .
```

this will bring up the container.open the http://localhost 

SUCCESS!!