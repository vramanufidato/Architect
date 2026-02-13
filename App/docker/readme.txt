Docker Concepts
Overview
Docker simplifies the process of creating, deploying, and managing applications by using containers. Containers allow you to package an application with its dependencies into a standardized unit for software development. Docker provides tools and a platform to build, ship, and run containers across various environments.

Dockerfile
A text file that contains instructions for building a Docker image. It specifies the base image, sets the working directory, installs dependencies, copies application code, exposes ports, and defines commands to run the application.

Container
An instance of a Docker image that runs as a process on the host machine. Containers are lightweight, portable, and isolated, making them ideal for deploying and scaling applications.

Docker Image Storage
Docker images are stored in registries, which can be public or private. Public registries like Docker Hub host millions of images, while organizations often use private registries for security and control.

Where Docker Images Exist
Local Machine: When you build a Docker image, it's initially stored locally on your machine. You can list local Docker images using the docker images command.



Understanding the Dockerfile
1: Base Image
Uses FROM openjdk:21-jdk-slim, which provides Java 21.

2: Working Directory
Sets /app as the working directory.

3: Labeling the Image
Adds metadata like maintainer name, version, and description.

4: Copying the Application
Copies myapp.jar (your Java web application) into the container.

5: Exposing Port 8080
Allows traffic to reach the application.

6: Running the Application
CMD runs the Java application using java -jar.

7: Health Check
Checks if the app is running at http://localhost:8080/health. If the request fails, Docker marks the container as unhealthy. Runs every 30s with 3 retries if the check fails.

Build the Docker Image
1
docker build -t my-java-app .

Copied!

Wrap Toggled!
Run the Container
1
docker run -p 8080:8080 my-java-app

Copied!

Wrap Toggled!
Check Container Health
1
docker ps --filter "health=unhealthy"