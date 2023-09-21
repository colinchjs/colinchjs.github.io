---
layout: post
title: "Running a basic Docker container"
description: " "
date: 2023-09-21
tags: [docker, containerization]
comments: true
share: true
---

In today's blog post, we will explore how to run a basic Docker container. Docker is an open-source platform that automates the deployment, scaling, and management of applications using containerization. Containers provide a lightweight, isolated environment for running applications across different platforms. Let's get started!

## Prerequisites

Before we begin, make sure you have Docker installed on your machine. You can download Docker from the official website based on your operating system.

## Creating a Docker Image

First, we need to create a Docker image. An image is a lightweight, standalone, and executable package that includes everything needed to run an application, including the code, runtime, libraries, and system tools. To create a Docker image, we use the Dockerfile.

Create a new directory and create a file named `Dockerfile` inside it. Open the Dockerfile in a text editor and add the following contents:

```Dockerfile
# Use an official Python runtime as the base image
FROM python:3.9-slim

# Set the working directory in the container
WORKDIR /app

# Copy the current directory contents into the container at /app
COPY . /app

# Install any dependencies
RUN pip install --no-cache-dir -r requirements.txt

# Expose a port
EXPOSE 8080

# Define the command to run the application
CMD ["python", "app.py"]
```

Make sure you have a Python file named `app.py` in the same directory as the Dockerfile. This is the entry point of your application.

## Building the Docker Image

To build the Docker image, open a terminal or command prompt, navigate to the directory containing the Dockerfile, and run the following command:

```bash
docker build -t myapp .
```

This command will build a Docker image named `myapp` using the Dockerfile in the current directory.

## Running the Docker Container

Now that we have a Docker image, we can run a Docker container based on that image. Run the following command to start a container from the `myapp` image:

```bash
docker run -d -p 8080:8080 myapp
```

This command will start a container in detached mode (`-d`) and map port `8080` from the host to port `8080` in the container. You can access the running application at `http://localhost:8080`.

## Conclusion

In this blog post, we learned how to run a basic Docker container. We covered creating a Docker image using a Dockerfile, building the image, and running a container. Docker provides an efficient and consistent way to package and deploy applications, making it easier to manage and scale your infrastructure. Stay tuned for more Docker-related topics in future blog posts!

#docker #containerization