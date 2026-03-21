# Flask App Deployment with CI/CD
# Project Overview
This project demonstrates deployment of a Flask web application using modern DevOps practices. The application is containerized using Docker, deployed on AWS EC2, and automated using CI/CD pipelines with GitHub Actions and Jenkins. Git is used for version control.

# Architecture Overview
The system consists of the following components:
Flask application (backend)
Docker for containerization
CI/CD pipeline (GitHub Actions / Jenkins)
AWS EC2 for hosting
GitHub repository for source code

# Workflow Explanation

1. Code Push
The developer pushes code changes to the GitHub repository. This triggers the CI/CD pipeline.

2. Continuous Integration (CI)
The CI pipeline performs the following steps:
Checks out the latest code from GitHub
Installs dependencies
Runs basic tests (if configured)
Builds a Docker image using the Dockerfile
Output: A ready-to-deploy Docker image

3. Docker Image Management
The Docker image is tagged appropriately
The image is pushed to a container registry (Docker Hub or similar)

4. Continuous Deployment (CD)
The deployment process includes:
Connecting to the AWS EC2 instance using SSH
Pulling the latest Docker image
Stopping and removing the old container
Running a new container with the updated image
Output: Updated application running on EC2

5. Application Access
The Flask application runs inside a Docker container on EC2
It is accessed via the EC2 public IP and exposed port

# Tools Used
### Flask
A lightweight Python web framework used to build the application
### Docker
Used to containerize the application for consistent deployment across environments
### AWS EC2
Provides a virtual server to host the application
### Git and GitHub
Used for version control and source code management
### GitHub Actions
Used to automate CI/CD pipelines directly from the repository
### Jenkins
Used as an alternative CI/CD tool for pipeline automation and control
# Dockerfile Explanation
### Typical steps included in the Dockerfile:
- Select a base Python image
- Set working directory
- Copy application files
- Install dependencies using requirements.txt
- Define the command to run the Flask app

# Key Features
- Automated CI/CD pipeline
- Containerized deployment using Docker
- Cloud deployment on AWS EC2
- Version-controlled workflow using Git
- Repeatable and consistent deployment process
- Security and Best Practices
- No sensitive data hardcoded in code
- Use of environment variables for configuration
- SSH key-based authentication for EC2 access
- Controlled access using security groups

# Challenges Faced
- Debugging Docker build issues
- Handling CI/CD pipeline failures
- Managing EC2 connectivity and permissions



