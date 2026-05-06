Building Custom Images with Dockerfile

Overview

This session focused on creating custom Docker images using a Dockerfile. Instead of relying on pre-built images, a custom image was built by defining a set of instructions to install and configure a web server (NGINX).

Objective
Understand the purpose of a Dockerfile
Build a custom Docker image
Run a container from the custom image
Deploy a web server using the created image


What is a Dockerfile
A Dockerfile is a configuration file that contains step-by-step instructions to build a Docker image. It automates the process of setting up an environment, installing dependencies, and defining the default behavior of a container.

Dockerfile Implementation
Dockerfile Content
FROM ubuntu
RUN apt update
RUN apt install -y nginx
CMD ["nginx", "-g", "daemon off;"]


Instruction Breakdown
FROM ubuntu -- Defines the base image for the build process
RUN apt update -- Updates the package list inside the image
RUN apt install -y nginx -- Installs the NGINX web server
CMD ["nginx", "-g", "daemon off;"] -- Specifies the default command to run when the container starts

Build Process
Build the custom image : docker build -t mynginx .
-t mynginx assigns a name to the image
. indicates the current directory containing the Dockerfile


Verification
Check available images : docker images

Run container from custom image : docker run -d -p 8085:80 mynginx
-d runs the container in background
-p 8085:80 maps host port 8085 to container port 80
