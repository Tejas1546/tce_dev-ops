# 01/04/2025 - Docker & Environment Overview

---

## Server Environments for Application Deployment

- **Development Environment (Dev)**: This is where developers test initial features and minimal test cases.
- **Testing Environment (Test)**: Used by testing teams to carry out both functional and non-functional tests, including performance testing and load testing.
- **User Acceptance Testing (UAT)**: Before the product is released, it's shown to the customer for feedback and approval.
- **Production Environment**: This is the live environment where the application is accessible to end-users.

---

## What is a Container?

- A container is essentially an isolated environment where we run our application. It bundles the application and its dependencies to run consistently across various computing environments.

---

## Key Docker Concepts

### Dockerfile

- A **Dockerfile** is a script that contains a series of instructions on how to build a Docker image and configure the container.

### Docker Image

- A **Docker image** is a snapshot of a file system and contains everything required to run an application, including:
  - Source code
  - Dependencies
  - Configurations
  - Libraries
  - Operating System layers
- The principle of **Build Once, Run Anywhere** means you can run the same image across different systems.

### Docker Hub

- **Docker Hub** is an online platform where Docker images are stored and shared.

---

## Essential Docker Commands

```bash
docker ps -a
# List all containers, regardless of whether they're running or not.

docker ps
# Only lists currently running containers.

service docker start
service docker status

docker create ubuntu /bin/bash
docker ps -a
docker ps

docker create -it --name webserver amazonlinux /bin/bash
docker start webserver
docker exec -it webserver /bin/bash
ls

docker run -it --name sample ubuntu /bin/bash

docker run -td --name web-app -p 3002:3000 muralisocial123/cart-page-test:1.0

# To exit from a detached container:
Ctrl + P + Q
```
### Port Binding (`-p` flag)

- The `-p` flag binds a container port to a port on the host machine, making it accessible externally.
  
- The port number can be chosen by the user, within the range of 0 to 65534.

---

## Detached Mode

- When a container runs in **detached mode**, it operates in the background as a daemon and doesn't occupy the terminal session.

---

## Dockerfile Instructions

### Build Commands

- `FROM`: Specifies the base image for the Docker container. Every Dockerfile must begin with this instruction.
  
- `COPY`: Copies files or directories from the host machine into the container.
  
- `ADD`: Similar to `COPY`, but can also download files from the internet directly into the container.
  
- `RUN`: Executes commands inside the container, commonly used for installing packages or dependencies.

### `.dockerignore`

- The `.dockerignore` file is used to exclude files or directories from being copied into the Docker image during the build process.

---

## Dockerfile Execution Commands

- `CMD`: Specifies the command to run when the container starts. It can include runtime arguments.
  
- `ENTRYPOINT`: Defines the main command for the container but does not allow runtime arguments.
  
- `EXPOSE`: Exposes a port for access to the container's service.
  
- `ENV`: Sets environment variables within the container.
  
- `WORKDIR`: Defines the working directory inside the container.
  
- `USER`: Specifies the user account for running the container.

---

## Purpose of the Dockerfile

- Collect necessary environment variables.
  
- Define the port number and database connection details for the container.

---

## Steps to Write a Dockerfile

1. Choose the base image for the application.
  
2. Set the working directory inside the container.
  
3. Copy necessary dependencies into the container.
  
4. Install the required packages.
  
5. Copy the source code from the host machine into the container.
  
6. Specify the port to expose for external access.
  
7. Set the command to run the application within the container.

---

## Example: Build & Push a Docker Image

```bash
git clone -b master https://github.com/Tejas1546/gitses.git
cd Dimple-CapsuleProject

docker build -t web-app-nodejs:1.0 .
docker images

docker run -td --name node-app -p 3015:3015 web-app-nodejs:1.0
docker ps
docker exec -it node-app /bin/bash

docker login
docker push tejas/web-app-nodejs:1.0
