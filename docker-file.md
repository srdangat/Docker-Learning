## What is Dockerfile
A Dockerfile is a script that contains instructions for building a customized docker image. Each instruction 
in a Dockerfile creates a new layer in the image, and the final image is composed of all the layers stacked 
on top of each other.

It includes instructions for installing dependencies, copying files, setting environment variables, and 
configuring the container.

Dockerfile uses a simple, easy-to-read syntax that can be created and edited with any text editor. Once a 
Dockerfile has been created, it can be used to build an image using the docker build command. The resulting 
image can then be run as a container using the docker run command.

## Explanation of Dockerfile Instructions

1. **FROM**
    - Define the base image, such as ubuntu or debian, used to start the build process.*Required* for each Dockerfile.
```
 FROM ubuntu:latest
```
2. **LABEL**
    - Adds metadata to the image, such as maintainer information or build details.
```
LABEL maintainer="your-email@example.com"
```
3. **ENV**
    - Set environment variables that persist when the container is deployed.
```
ENV SDLC_ENV=${SDLC_ARG}
```
4. **ARG**
    - It is only available during the build of a Docker image (RUN etc), not after the image is created and containers are started from it.It is used to Pass a variable during Image build.
```
ARG SDLC_ARG
```
5. **WORKDIR**
    - Sets the working directory inside the container, where all subsequent commands will be executed.
```
WORKDIR /opt/apache-tomcat-9.0.91
```
6. **COPY**
    - Copies files or directories from the host machine to the container.
```
COPY context.xml ./apache-tomcat-9.0.91/conf/context.xml
```
7. **RUN**
    - Executes commands in the container, commonly used to install software packages or dependencies.
```
RUN apt update -y
```
8. **ADD**
    - Adds files, directories, or remote file URLs to the container, similar to COPY but with additional capabilities like extracting tar files.
```
ADD apache-tomcat-9.0.91.tar.gz /opt/
```
9. **EXPOSE**
    - Expose a specific port to enable networking between the container and the Host.
```
EXPOSE 8080
```
10. **USER**
    - Sets the user to run the container processes, enhancing security by avoiding running as the root user.
```
USER sanket
```
11. **CMD**
    - Execute a specific command within the container that is deployed with the image. Only one is used per Dockerfile.
```
CMD ["run"]
```
12. **ENTRYPOINT**
    - Set a default application to be used every time a container is deployed with the image. Only one is used per Dockerfile.Higer priority over CMD
```
ENTRYPOINT ["/opt/apache-tomcat-9.0.91/bin/catalina.sh"]
```