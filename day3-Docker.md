Docker Day 3


Topics Covered
Ephemeral nature of containers
Data persistence in Docker
Docker volumes
Bind mounts
Volume vs Bind Mount comparison
Container Data Behavior

Containers are temporary (ephemeral). Any data created inside a container is lost when the container is removed.

Example:

Create a file inside a container
Stop and remove the container
Run a new container
The file no longer exists

This happens because containers do not store data permanently.

Docker Volumes

A Docker volume is a persistent storage mechanism managed by Docker. It allows data to remain even after containers are deleted.

Commands Practiced

Create a volume: docker volume create myvolume
List volumes: docker volume ls
Run container with volume: docker run -it -v myvolume:/data ubuntu bash


Volume Mount Explanation

Command used:
docker run -it -v myvolume:/data ubuntu bash

myvolume = volume on host (managed by Docker)
/data = directory inside container

This creates a connection between the Docker-managed volume and the container directory.

Bind Mount

Bind mount connects a directory from the host system directly to the container.

Command:

docker run -it -v /home/mohan/data:/data ubuntu bash
/home/mohan/data = directory on host
/data = directory inside container
