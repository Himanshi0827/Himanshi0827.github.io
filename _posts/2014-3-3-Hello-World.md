---
layout: post
title: Setting Up a Multi-Container Application with Docker
---

## Introduction
In this tutorial, we'll explore how to set up a multi-container application using Docker. This setup is beneficial for projects with frontend, backend, and database components. We'll use React for the frontend, Node.js for the backend, and MySQL for the database.

### Prerequisites
Before we begin, ensure you have the following prerequisites:
- Docker installed on your machine
- Basic understanding of Docker concepts
- Knowledge of your application's frontend and backend technologies


## Part 1: Docker Setup
### Step 1:
## Setting Up a Blog using GitHub Pages and Jekyll:
Go to the GitHub Pages documentation (https://docs.github.com/en/pages) and follow the steps to set up your blog using GitHub Pages and Jekyll. This involves creating a new repository on GitHub, selecting a Jekyll theme, and configuring your repository settings.
Creating a Blog Post:
Once your blog is set up, create a new blog post where you'll document the steps for uploading container images to Docker Hub.
![Containers]({{ site.baseurl }}/images/Screenshot (351).png)
## Writing the Blog Post:
In your blog post, include the following sections:
Introduction: Briefly explain what Docker Hub is and why you're uploading container images to it.
### Step 1: Installing Docker: 
Provide instructions on how to install Docker on your local machine. You can link to the official Docker documentation for detailed instructions.
### Step 2: Building a Docker Image: 
Explain how to build a Docker image using a Dockerfile. You can use a simple example like a "Hello World" application.
![Containers]({{ site.baseurl }}/images/Screenshot (324).png)
![Containers]({{ site.baseurl }}/images/Screenshot (325).png)
![Containers]({{ site.baseurl }}/images/Screenshot (326).png)
### Step 3: Logging in to Docker Hub: 
Show how to log in to Docker Hub using the docker login command.
### Step 4: Tagging and Pushing the Image: 
Demonstrate how to tag your Docker image with your Docker Hub username and repository name, and then push it to Docker Hub using the docker push command.
Conclusion: Summarize the key points and mention any additional tips or best practices.
### Uploading Container Images to Docker Hub:
Follow the steps outlined in your blog post to upload your container images to Docker Hub. Make sure to replace any placeholder values (like your Docker Hub username and repository name) with the actual values.
### Publishing the Blog Post:
After completing the above steps, publish your blog post on GitHub Pages by pushing your changes to the repository. Make sure the post is live and accessible via your GitHub Pages URL.

### Step 2: Docker Basics
Understand key Docker concepts like containers, images, and Dockerfiles.

## Part 2: Creating Docker Images
### Step 3: Frontend Dockerfile
Create a Dockerfile for the React frontend:
```Dockerfile
# Use official Node.js image as the base image
FROM node:14-alpine

# Copy package.json and package-lock.json files to the working directory
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy all files to the working directory
COPY . .

# Build the React app for production
RUN npm run build

# Expose port 80 to the outside world
EXPOSE 3000


# Command to run the application
CMD ["npm", "start"]
```

### Step 4: Backend Dockerfile
Create a Dockerfile for the Node.js backend:
```Dockerfile
# Use official Node.js image as the base image
FROM node:14-alpine

# Copy package.json and package-lock.json files to the working directory
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy all files to the working directory
COPY . .

# Expose port 5000 to the outside world
EXPOSE 5000

# Command to run the application
CMD ["node", "server.js"]
```

### Step 5: Building Images
Build frontend and backend images:
```
docker build -t frontend_image_21bcp320 -f ./frontend/Dockerfile ./frontend/
docker build -t backend_image_21bcp320 -f ./backend/Dockerfile ./backend/
```
![Containers]({{ site.baseurl }}/images/Screenshot (341).png)
![Containers]({{ site.baseurl }}/images/Screenshot (343).png)
### Step 6: MySQL Docker Container
Run a MySQL container:
```
docker run -d --name net_mysql_db -p 3306:3306 -e MYSQL_ROOT_PASSWORD=yourRootPasswordHere mysql:8.0
```
Create database and tables inside the container.
![Containers]({{ site.baseurl }}/images/Screenshot (344).png)
![Containers]({{ site.baseurl }}/images/Screenshot (345).png)
## Part 3: Running the Application
![Containers]({{ site.baseurl }}/images/Screenshot 2024-04-23 193704.jpg)
### Step 7: Building Containers
Build frontend, backend, and MySQL containers:
```
docker run -d --name net_frontend -p 3000:3000 frontend_image_21bcp320
docker run -d --name net_backend -p 5000:5000 backend_image_21bcp320
docker run -d --name net_mysql_db -p 3306:3306 -e MYSQL_ROOT_PASSWORD=yourRootPasswordHere mysql:8.0
```
![Containers]({{ site.baseurl }}/images/Screenshot (329).png)
![Containers]({{ site.baseurl }}/images/Screenshot (340).png)
![Containers]({{ site.baseurl }}/images/Screenshot (341).png)
![Containers]({{ site.baseurl }}/images/Screenshot (343).png)
![Containers]({{ site.baseurl }}/images/Screenshot (344).png)
![Containers]({{ site.baseurl }}/images/Screenshot (349).png)
![Containers]({{ site.baseurl }}/images/Screenshot (350).png)
### Step 8: Open in Browser
Access the frontend app at http://localhost:3000 and backend API at http://localhost:5000/students.

Adjust the placeholders with your actual values. Happy Dockerizing!
```
![Containers]({{ site.baseurl }}/images/Screenshot 2024-04-23 193704.jpg)
![Containers]({{ site.baseurl }}/images/Screenshot (352).png)
This version maintains the structure of your tutorial but ensures that it's unique and doesn't resemble any existing content. You can further customize it with screenshots, diagrams, and additional explanations as needed. Let me know if there's anything else you'd like to add or modify!
