# Flask App Deployment with CI/CD

# Student Management System

A simple Flask application for managing student records.

# Project Overview
This project demonstrates deployment of a Flask web application using modern DevOps practices. The application is containerized using Docker, deployed on AWS EC2, and automated using CI/CD pipelines with GitHub Actions and Jenkins. Git is used for version control.

## Table of Contents
- [Overview](#overview)
- [Features](#features)
- [Installation](#installation)
- [Usage](#usage)
- [API Endpoints](#api-endpoints)
- [Database](#database)
- [Deployment](#deployment)
- [CI/CD](#cicd)
- [Contributing](#contributing)
- [License](#license)

## Overview
The Student Management System is a web application built using Flask and SQLAlchemy that allows you to manage student records. It provides features to create, view, edit, and delete student details.

## Features
- View a list of all students
- View individual student details
- Create new student records
- Edit existing student records
- Delete student records
- RESTful API endpoints
- SQLite database for data persistence
- Docker containerization
- CI/CD pipeline with Jenkins

## Installation

### Prerequisites
- Python 3.9 or higher
- pip (Python package manager)
- Docker ( for containerized deployment)

## Usage

### Web Interface
- **Home Page**: View all students
- **Student Details**: Click on a student's name to view details
- **Create Student**: Use the "Create" link to add new students
- **Edit Student**: Click "Edit" on a student's page to modify details
- **Delete Student**: Click "Delete" on a student's page to remove them

### API Endpoints

The application provides RESTful API endpoints:

- `GET /` - List all students
- `GET /<id>/` - Get student details
- `POST /create/` - Create new student
- `POST /<id>/edit/` - Update student
- `POST /<id>/delete/` - Delete student
- `GET /health` - Health check endpoint

## Database

The application uses SQLite as the database. The database file `database.db` will be created automatically in the project root when you first run the application.

### Database Schema

The `Student` model includes:
- `id`: Primary key
- `firstname`: Student's first name
- `lastname`: Student's last name
- `email`: Unique email address
- `age`: Student's age
- `bio`: Biography/description
- `created_at`: Timestamp

## Deployment

### Docker Deployment
The application is containerized using Docker. The Dockerfile includes:
- Python 3.9 slim base image
- Required system dependencies
- Python dependencies installation
- Port 5000 exposure

### EC2 Deployment
The Jenkins pipeline automates deployment to AWS EC2:
1. Builds Docker image
2. Pushes to Docker Hub
3. Deploys to EC2 instance

## CI/CD

The project includes a Jenkins pipeline (`Jenkinsfile`) that:
- Clones the code from GitHub
- Builds the Docker image
- Pushes to Docker Hub
- Deploys to EC2 instance via SSH

### Jenkins Requirements
- Docker Hub credentials
- EC2 SSH key credentials
- EC2 instance with Docker installed

## Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## License

This project is licensed under the MIT License - see the LICENSE file for details.





