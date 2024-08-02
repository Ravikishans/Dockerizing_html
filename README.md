# Dockerized Nginx with Simple HTML Page

## Overview

This project demonstrates how to Dockerize a simple HTML page using Nginx as the web server.

## Files

### index.html
A basic HTML page with the content "Hello, Docker!".

### nginx.conf
Nginx configuration file to serve the `index.html` page.

### Dockerfile
Defines the Docker image:
- Uses the official Nginx base image.
- Copies `nginx.conf` and `index.html` to the appropriate locations in the container.
- Exposes port 80 and starts the Nginx server.

### Docker-compose.yml
Defines the Docker Compose setup for building and running the container.

## Steps to Build and Run the Docker Container

### Using Docker

1. Build the Docker image:
    ```sh
    docker build -t ravikishans/htmlfile:latest .
    ```

2. Run the Docker container:
    ```sh
    docker run -d -p 80:80 ravikishans/htmlfile:latest
    ```

3. Access the webpage by navigating to `http://localhost` in your web browser.

### Using Docker Compose

1. Build and run the Docker container using Docker Compose:
    ```sh
    docker-compose up -d
    ```

2. Access the webpage by navigating to `http://localhost` in your web browser.

## Pushing the Image to ECR

1. Authenticate Docker to the ECR registry:
    ```sh
    aws ecr-public get-login-password --region ap-northeast-2 | docker login --username AWS --password-stdin 975050024946.dkr.ecr.ap-northeast-2.amazonaws.com
    ```

2. Tag your Docker image:
    ```sh
    docker tag ravikishans/htmlfile:latest 975050024946.dkr.ecr.ap-northeast-2.amazonaws.com/ravidockerassign:latest
    ```

3. Push the image to your ECR repository:
    ```sh
    docker push 975050024946.dkr.ecr.ap-northeast-2.amazonaws.com/ravidockerassign:latest
    ```

## Public ECR Repository

You can find the public ECR repository at the following link:
[public.ecr.aws/f8g8h5d4/ravidockerassign:latest](#)
