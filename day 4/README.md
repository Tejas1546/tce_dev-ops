# 01/04/2025 - Docker & Environment Notes

---

## Environment - Server (Run our Application)

- **Dev Environment** — Used by developers to perform basic testing and validations.
- **Test Environment** — QA teams run both functional and non-functional test cases (e.g., performance, load testing).
- **UAT Environment** — User Acceptance Testing: The application is reviewed by clients before it goes live.
- **Production Environment** — Live environment where real users access the application.

---

## What is a Container?

- A container is a lightweight, standalone executable unit where applications run with their dependencies packaged.

---

## Docker Concepts

### Dockerfile

- A script with instructions on how to build a Docker image for your application.

### Docker Image

- A read-only template containing everything needed to run the application:
  - Code
  - Dependencies
  - Config files
  - Libraries
  - Environment setup  
- **Build Once, Run Anywhere**

### Docker Hub

- A cloud-based repository for sharing and storing Docker images.

---

## Useful Docker Commands

```bash
docker ps -a
# Lists all containers (running and stopped)

docker ps
# Lists only currently running containers

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

# To detach from container without stopping:
Ctrl + P + Q
```
### 🔌 Port Mapping with `-p` Flag

- Used to connect the container's internal port to a port on the host machine.
- Syntax: `-p <hostPort>:<containerPort>`
- You can choose any port between **0–65535**, as long as it's not already in use.

---

## 🧱 Detached Mode (Background Running)

- Also called **Daemon Mode**
- Run a container in the background using the `-d` flag.

```bash
docker run -td --name container-name image-name
```
## 🛠️ Dockerfile Instructions

---

### 🧱 Build-Time Instructions

- `FROM` – Sets the base image for the Docker container.
- `COPY` – Transfers files or directories from your system into the image.
- `ADD` – Similar to `COPY`, but also supports URLs and archive extraction.
- `RUN` – Executes commands to install packages or configure the image during the build process.

---

### 📄 `.dockerignore` File

- Functions like `.gitignore`
- Used to exclude files or folders from being added during the image build process.

---

## 🏃 Runtime Instructions

- `CMD` – Specifies the default command to run when the container starts (can be overridden).
- `ENTRYPOINT` – Defines the primary command that always executes in the container.
- `EXPOSE` – Indicates the port on which the container listens.
- `ENV` – Sets environment variables.
- `WORKDIR` – Sets the working directory within the container.
- `USER` – Defines the user that the container runs as.

---

## 🧩 Role of Docker Configuration

Docker containers are often configured with:

- Environment Variables
- Application Ports
- Database Endpoints or Connection Strings

---

## ✍️ Steps to Write a Dockerfile

1. Define the base image using `FROM`.
2. Set the working directory using `WORKDIR`.
3. Use `COPY` or `ADD` to transfer required files into the container.
4. Install dependencies with `RUN`.
5. Add your application code to the image.
6. Use `EXPOSE` to declare the container's port.
7. Use `CMD` or `ENTRYPOINT` to specify the start-up command.

---

## 🚀 Build and Push Docker Image – Example

```bash
# Clone the project repository
git clone -b master https://github.com/Tejas1546/gitses.git
cd Dimple-CapsuleProject

# Build the Docker image
docker build -t web-app-nodejs:1.0 .

# View the created image
docker images

# Run the container from the image
docker run -td --name node-app -p 3015:3015 web-app-nodejs:1.0

# List running containers
docker ps

# Enter the running container's shell
docker exec -it node-app /bin/bash

# Login to Docker Hub and push the image
docker login
docker push tejas/web-app-nodejs:1.0
```