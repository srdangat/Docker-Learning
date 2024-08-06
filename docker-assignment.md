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

### Part 2: Building and Managing Custom Images

1. **Create a Simple Web Application**
   - **Task**: Create a directory for your project and a simple web application as described in the previous assignment.
   - **Solution**:
     Create a directory named `my-web-app` and navigate into it. Inside this directory, create a file named `app.py` with the following content:
     ```python
     from flask import Flask

     app = Flask(__name__)

     @app.route('/')
     def hello_world():
         return 'Hello, Docker!'

     if __name__ == '__main__':
         app.run(host='0.0.0.0', port=5000)
     ```
     Create a `requirements.txt` file with the following content:
     ```plaintext
     Flask==1.1.2
     Werkzeug==1.0.1
     Jinja2==2.11.3
     MarkupSafe==1.1.1
     itsdangerous==1.1.0
     ```

2. **Create a Dockerfile**
   - **Task**: Create a `Dockerfile` for the web application as described in the previous assignment.
   - **Solution**:
     Create a file named `Dockerfile` in the `my-web-app` directory with the following content:
     ```dockerfile
     # Use the official lightweight Python image from the Docker Hub
     FROM python:3.9-slim

     # Set the working directory in the container
     WORKDIR /app

     # Install gcc and other necessary dependencies
     RUN apt-get update && apt-get install -y --no-install-recommends \
         gcc \
         && rm -rf /var/lib/apt/lists/*

     # Copy the requirements file into the container
     COPY requirements.txt .

     # Install the required packages
     RUN pip install --no-cache-dir -r requirements.txt

     # Copy the rest of the application code into the container
     COPY . .

     # Expose port 5000 for the Flask app
     EXPOSE 5000

     # Run app.py when the container launches
     CMD ["python", "app.py"]
     ```  

3. **Build a Docker Image**
   - **Task**: Build a Docker image for your web application.
   - **Command**:
     ```sh
     docker build -t my-web-app .
     ```
   - **Solution Explanation**: This command builds a Docker image named `my-web-app` from the `Dockerfile` in the current directory (`.`).

4. **Tag a Docker Image**
   - **Task**: Tag your image with a specific version (e.g., `my-web-app:v1.0`).
   - **Command**:
     ```sh
     docker tag my-web-app my-web-app:v1.0
     ```
   - **Solution Explanation**: This command tags the `my-web-app` image with the version `v1.0`.

5. **Run a Docker Container from Custom Image**
   - **Task**: Run a container from your custom image and map the necessary ports.
   - **Command**:
     ```sh
     docker run -d -p 5000:5000 my-web-app
     ```
   - **Solution Explanation**: This command runs the `my-web-app` container in detached mode (`-d`) and maps port 5000 of the container to port 5000 on the host machine (`-p 5000:5000`).

6. **Push the Image to Docker Hub**
   - **Task**: Push your tagged image to Docker Hub (requires a Docker Hub account).
   - **Command**:
     ```sh
     docker tag my-web-app:v1.0 <your_dockerhub_username>/my-web-app:v1.0
     docker push <your_dockerhub_username>/my-web-app:v1.0
     ```
   - **Solution Explanation**: Replace `<your_dockerhub_username>` with your Docker Hub username. The first command tags the image for Docker Hub, and the second command pushes the image to your Docker Hub repository.