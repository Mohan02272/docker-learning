# Docker Day 5: Docker Layers, Cache, and Image Optimization


This session focused on understanding how Docker images are built internally using layers, how Docker caching improves build performance, and how to optimize Dockerfiles to create smaller and more efficient images.

##  Docker Image Layers

Every instruction in a Dockerfile creates a separate layer in the final image. These layers are stacked on top of each other to form the complete image.

Example Dockerfile:

FROM ubuntu
RUN apt update
RUN apt install -y nginx

Layer breakdown:

Base layer: Ubuntu image
Layer 1: apt update
Layer 2: Installation of NGINX

Each instruction creates a new layer, and Docker stores them independently.

## Viewing Image Layers

To inspect how an image is built and see its layers:

docker history mynginx

This command shows:

Each layer of the image
The command used to create it
Size of each layer

This helps identify which instructions increase image size.

## Docker Cache Mechanism

Docker uses caching to speed up the build process. If a layer has not changed since the last build, Docker reuses the existing layer instead of rebuilding it.

Example:

If RUN apt update has already been executed before, Docker will reuse the cached result during the next build.

To observe cache behavior:

docker build -t mynginx .

If caching is used, you will see the word “CACHED” in the output.

##  Problem with Inefficient Dockerfiles

Poorly written Dockerfiles create large images and slow builds.

Example of inefficient Dockerfile:

FROM ubuntu

RUN apt update
RUN apt install -y nginx
RUN apt install -y curl
RUN apt install -y vim

Problems:

Multiple layers increase image size
Redundant package installation steps
Slower build performance

##  Optimized Dockerfile

A better approach is to combine commands and reduce layers.

Example:

FROM ubuntu

RUN apt update && \
    apt install -y nginx curl vim && \
    apt clean

CMD ["nginx", "-g", "daemon off;"]

Improvements:

Fewer layers
Smaller image size
Faster build process
Cleanup reduces unnecessary files

## Build Optimized Image
docker build -t optimized-nginx .

This creates a more efficient Docker image compared to the previous version.

## Comparing Images

To compare images and understand size differences:

docker images

This helps identify which image is optimized and lighter.
