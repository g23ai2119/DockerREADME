# DockerREADME
# Sample Web Application Deployment Using Docker Containers

## Author
- **ANAS KHAN:** G23AI2119

## Introduction
This README file details the process of deploying a sample web application using Docker containers. The deployment involves creating Docker images from scratch, without using any existing Docker container images.

## Application Functionality
The sample web application is a simple Python Flask app that returns a "Hello, World!" message when accessed via a web browser.

## Steps to Deploy the Application

### Step 1: Set Up the Application
1. **Create a new directory for the project:**
    ```bash
    mkdir sample-web-app
    cd sample-web-app
    ```

2. **Create a Python script for the Flask app:**
    - **app.py**
    ```python
    from flask import Flask

    app = Flask(__name__)

    @app.route('/')
    def hello_world():
        return 'Hello, World!'

    if __name__ == '__main__':
        app.run(host='0.0.0.0', port=5000)
    ```

3. **Create a requirements file for the dependencies:**
    - **requirements.txt**
    ```
    Flask==2.0.3
    ```

### Step 2: Create a Dockerfile
1. **Create a Dockerfile in the project directory:**
    - **Dockerfile**
    ```dockerfile
    # Use an official Python runtime as a parent image
    FROM python:3.9-slim

    # Set the working directory in the container
    WORKDIR /usr/src/app

    # Copy the current directory contents into the container at /usr/src/app
    COPY . .

    # Install any needed packages specified in requirements.txt
    RUN pip install --no-cache-dir -r requirements.txt

    # Make port 5000 available to the world outside this container
    EXPOSE 5000

    # Define environment variable
    ENV FLASK_APP=app.py

    # Run app.py when the container launches
    CMD ["flask", "run", "--host=0.0.0.0"]
    ```

### Step 3: Build the Docker Image
1. **Build the Docker image using the Dockerfile:**
    ```bash
    docker build -t sample-web-app .
    ```

### Step 4: Run the Docker Container
1. **Run the container from the image:**
    ```bash
    docker run -d -p 5000:5000 sample-web-app
    ```

2. **Verify the container is running:**
    ```bash
    docker ps
    ```

### Step 5: Access the Application
1. **Open a web browser and navigate to:**
    ```
    http://localhost:5000
    ```

2. **You should see the "Hello, World!" message displayed on the page.**

## Conclusion
This document provided a step-by-step guide to deploy a simple Flask web application using Docker containers. The Docker image was created from scratch, without the use of any existing Docker container images. The application is now running in a Docker container and can be accessed via a web browser.

## Author Details
- *ANAS KHAN* *g23ai2119*
