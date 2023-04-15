# Agenda

1. Introduction
2. Installing Docker
   - on Windows
   - on Debian/Ubuntu-Derivatives
   - on Arch-Derivatives
3. Deploying a simple HTML-Website using Docker
4. Creating a Dockerfile

---

# Introduction

## What is Docker and Why?
Docker is a platform designed to help developers build, share, and run modern applications. 

## Terminology of Docker
Docker pagages software into standardized units called containers that have everything the software needs to run including libraries, system tools, code, and runtime

### Images
Docker images are the basis of containers. An Image is an ordered collection of root filesystem changes and the corresponding execution parameters for use within a container runtime. 
An image typically contains a union of layered filesystems stacked on top of each other. An image does not have state and it never changes.

### Containers
A container is a runtime instance of a docker image.

A Docker container consists of
- A Docker image 
- An execution environment 
- A standard set of instructions

The concept is borrowed from shipping containers, which define a standard to ship goods globally. Docker defines a standard to ship software.

### Compose/docker-compose
Compose is a tool for defining and running complex applications with Docker. With Compose, you define a multi-container application in a single file, 
then spin your application up in a single command which does everything that needs to be done to get it running.


### Entrypoint
In a Dockerfile, an ENTRYPOINT is an optional definition for the first part of the command to be run. 
If you want your Dockerfile to be runnable without specifying additional arguments to the docker run command, you must specify either ENTRYPOINT, CMD, or both.

---

# Installing Docker

### Track A: Windows

https://docs.docker.com/desktop/install/windows-install/

### Tack B: Linux/Debian-Derivate
```
sudo apt-get update
sudo apt-get install \
    ca-certificates \
    curl \
    gnug
    
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

sudo docker run hello-world
```
https://www.geeksforgeeks.org/how-to-install-and-configure-docker-on-arch-based-linux-distributionsmanjaro/
https://docs.docker.com/engine/install/ubuntu/

### Track C: Linux/Arch-Derivate
```
sudo pacman -Syu

sudo pacman -S docker

sudo docker version

sudo systemctl start docker.service
sudo systemctl status docker.service
```
https://docs.docker.com/desktop/install/archlinux/

---

# Deploy a simple HTML-Website using Docker

### Create a Website
Create a basic HTML-Website saying Hello World! Like ./website

### Publish Website using nginx via docker run
--name: Name of the container
--publish/-p: Publish a container’s port(s) to the host
--volume/-v: Bind mount a volume 
--detach/-d: Run container in background and print container ID

docker run \ 
--name hello-world
-p 8080:80
-v ./website:/usr/share/nginx/html:ro
-d nginx

###  Publish Website using nginx via docker-compose
Build a docker-compose file like in docker-direct.yml

---

# Creating a Dockerfile
Write a Dockerfile like in ./website/Dockerfile
Deploy it using a docker-compose file like in docker-build.yml

---

# More Information:

### Docker-Basics:
https://docs.docker.com/
https://docs.docker.com/glossary/

### Docker-Hub (get Software)
https://hub.docker.com/

### NGINX
https://nginx.org/en/docs/
