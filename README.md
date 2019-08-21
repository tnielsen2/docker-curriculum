Docker Curriculum
===

> Learn to build and deploy your distributed applications easily to the cloud with Docker

Forked repo for simple containers used for testing Ansible ECS task definitions.

## flask-app

A flask container that will show cat gifs from Buzzfeed.


```
docker run -d -p 5000:5000 flask:demo
```

## static-site

Nginx container with a static website.

```
docker run -d -p 80:80 static-site:demo
```
