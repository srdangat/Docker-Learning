# Docker Basic Commands Assignment

## Objective
- Learn and practice basic Docker commands for managing images,containers,and Docker environments.

## Prerequisites
- Docker installed on your machine (Docker Desktop for Windows/Mac or Docker Engine for Linux).

## Assignment

### Part 1: Docker Images and Containers

1. **Pull an Image from Docker Hub**
   - **Task**: Pull the official `nginx` image from Docker Hub.
   - **Command**:
     ```sh
     docker pull nginx
     ```
   - **Solution Explanation**: This command downloads the `nginx` image from Docker Hub to your local machine.

2. **List Docker Images**
   - **Task**: List all Docker images on your local machine.
   - **Command**:
     ```sh
     docker images
     ```
   - **Solution Explanation**: This command displays a list of all Docker images currently stored on your machine.

3. **Run a Docker Container**
   - **Task**: Run a container using the `nginx` image and map port 80 of the container to port 8080 on your host machine.
   - **Command**:
     ```sh
     docker run -d -p 8080:80 nginx
     ```
   - **Solution Explanation**: This command runs the `nginx` container in detached mode (`-d`) and maps port 80 of the container to port 8080 on the host machine (`-p 8080:80`).

4. **List Running Containers**
   - **Task**: List all running Docker containers.
   - **Command**:
     ```sh
     docker ps
     ```
   - **Solution Explanation**: This command lists all currently running Docker containers.

5. **Inspect a Running Container**
   - **Task**: Inspect the running `nginx` container to view detailed information.
   - **Command**:
     ```sh
     docker inspect <container_id>
     ```
   - **Solution Explanation**: Replace `<container_id>` with the actual container ID from the `docker ps` command. This command provides detailed information about the specified container.

6. **Stop a Running Container**
   - **Task**: Stop the running `nginx` container.
   - **Command**:
     ```sh
     docker stop <container_id>
     ```
   - **Solution Explanation**: Replace `<container_id>` with the actual container ID from the `docker ps` command. This command stops the specified running container.

7. **Remove a Container**
   - **Task**: Remove the stopped `nginx` container.
   - **Command**:
     ```sh
     docker rm <container_id>
     ```
   - **Solution Explanation**: Replace `<container_id>` with the actual container ID from the `docker ps -a` command. This command removes the specified container.

8. **Remove a Docker Image**
   - **Task**: Remove the `nginx` image from your local machine.
   - **Command**:
     ```sh
     docker rmi nginx
     ```
   - **Solution Explanation**: This command removes the `nginx` image from your local machine.