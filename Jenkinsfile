pipeline {
    agent any

    environment {
        DOCKERHUB_CREDENTIALS = credentials('dockerhub-creds')
        EC2_USER = 'ubuntu'
        EC2_HOST = '54.235.234.64'
    }

    stages {
        stage('Clone Code') {
            steps {
                git branch: 'main', url: 'https://github.com/Harshitha-Galla5/APSSDC-PROJECT.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t harshitha30galla/apssdc-flask-app:latest .'
            }
        }

        stage('Push to Docker Hub') {
            steps {
                sh "echo ${DOCKERHUB_CREDENTIALS_PSW} | docker login -u ${DOCKERHUB_CREDENTIALS_USR} --password-stdin"
                sh 'docker push harshitha30galla/apssdc-flask-app:latest'
            }
        }

        stage('Deploy to EC2') {
            steps {
                sshagent(credentials: ['ec2-ssh-key']) {
                    sh """
                    ssh -o StrictHostKeyChecking=no ${EC2_USER}@${EC2_HOST} \\
                      "sudo docker stop apssdc-container || true && \\
                       sudo docker rm apssdc-container || true && \\
                       sudo docker pull harshitha30galla/apssdc-flask-app:latest && \\
                       sudo docker run -d --name apssdc-container -p 5000:5000 harshitha30galla/apssdc-flask-app:latest"
                    """
                }
            }
        }
    }
}
