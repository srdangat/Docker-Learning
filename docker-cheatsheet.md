## General Commands

```sh
docker --version
docker info
docker version
docker help
```

## Container Management

## Run a Docker Container in Detach Mode
```sh
docker run -d --name my_container nginx
```
## Start a Stopped Container
```sh
docker start my_container
```
## Stop a Running Container
```sh
docker stop my_container
```
## Restart a Container
```sh
docker restart my_container
```
## Pause a Running Container
```sh
docker pause my_container
```
## Unpause a Paused Container
```sh
docker unpause my_container
```
## Kill a Running Container
```sh
docker kill my_container
```
## Remove a Stopped Container
```sh
docker rm my_container
```
## Execute a Command in a Running Container
```sh
docker exec -it my_container /bin/bash
```
## Attach to a Running Container
```sh
docker attach my_container
```
## View Logs of a Container
```sh
docker logs my_container
```
## Inspect a Container
```sh
docker container inspect my_container
```
## Copy Files from a Container to Local Machine
```sh
docker cp my_container:/path/to/file /local/path
```
## Copy Files from Local Machine to a Container
```sh
docker cp /local/path my_container:/path/to/file
```
## Map Ports When Running a Docker Container
```sh
docker run -d -p host_port:container_port --name my_container nginx
```
## Stop All Running Containers
```sh
docker stop $(docker ps -q)
```
## Remove All Stopped Containers
```sh
docker container prune
```
## Force Remove All Containers (Running and Stopped)
```sh
docker rm -f $(docker ps -a -q)
```

## Image Management

## Downloads a Docker image from a Docker registry (usually Docker Hub).
```sh
docker pull <image_name>:<tag>
```
## Lists all Docker images on your local machine.
```sh
docker images
```
## Removes one or more Docker images from your local machine.
```sh
docker rmi <image_name>:<tag>
```
## Shows detailed information about Docker objects (containers, images, volumes, etc.).
```sh
docker inspect
```