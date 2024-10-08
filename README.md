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
    aws ecr-public get-login-password --region us-east-1 | docker login --username AWS --password-stdin public.ecr.aws/f8g8h5d4
    ```
   # Error handeling  
   If the login fails getting error like-- `Error saving credentials: error storing credentials - err: exit status 1, out: error storing credentials - err: exit status 1, out: The stub received bad data.`
   
    Then--
    Ensure Docker is not using an external credential store that might cause this issue. To disable the Docker credential store:
    Open` ~/.docker/config.json `(if present in your WSL2 environment).
    Remove or comment out the line:
`
    "credsStore": "wincred"
`   
    Save the file and try running the login command again.
    
2. Build and Tag your Docker image:
    ```sh
   docker build -t ravidockerassign .
    ```

    ```sh
   docker tag ravidockerassign:latest public.ecr.aws/f8g8h5d4/ravidockerassign:latest

    ```

3. Push the image to your ECR repository:
    ```sh
    docker push public.ecr.aws/f8g8h5d4/ravidockerassign:latest
    ```

## Public ECR Repository

You can find the public ECR repository at the following link:
[public.ecr.aws/f8g8h5d4/ravidockerassign:latest](#)
