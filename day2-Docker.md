# Docker Day 2

## Docker Images
Pulling images from Docker Hub
Running real application (NGINX)
Port mapping (Host vs Container)
Docker Image Concept

A Docker image is a read-only template that contains:

## Operating system
Application software
Required dependencies

Images are used to create containers. A container is a running instance of an image.

## Commands Practiced

Pull NGINX image

docker pull nginx

Check available images

docker images

Run NGINX container with port mapping

docker run -d -p 8080:80 nginx

Check running containers

docker ps

Stop container

docker stop <container_id>

Remove container

docker rm <container_id>

Port Mapping Explanation

Command used:

docker run -d -p 8080:80 nginx
8080 = Host port (local machine)
80 = Container port (inside Docker)

This means:
Requests coming to port 8080 on the host machine are forwarded to port 80 inside the container where NGINX is running.

How Request Flows

Browser request:

http://localhost:8080

## Flow:

Browser sends request to host port 8080
Docker forwards request to container port 80
NGINX processes the request and returns response
Key Learnings
Docker images are templates used to create containers
Containers run applications in isolated environments
Port mapping allows external access to container services
Multiple containers can run on different host ports using the same internal port
Practical Outcome
Successfully pulled NGINX image
Deployed a running web server inside a container
Accessed the web server through browser using port mapping
Notes
First image pull downloads from Docker Hub
Containers run independently from host system
Port mapping is required to expose container services
