pipeline {
    agent any

    environment {
        DOCKER_HUB_USERNAME = 'your_dockerhub_username'
        DOCKER_HUB_REPO = 'your_dockerhub_repo'
        DOCKER_HUB_PASSWORD = credentials('docker-hub-credentials')
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/usaydatheri200907/scdlab11'
            }
        }

        stage('Dependency Installation') {
            steps {
                sh 'npm install'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh "docker build -t \${DOCKER_HUB_REPO}:latest ."
            }
        }

        stage('Run Docker Image') {
            steps {
                sh "docker run -d -p 80:80 \${DOCKER_HUB_REPO}:latest"
            }
        }

        stage('Push Docker Image') {
            steps {
                sh "echo \${DOCKER_HUB_PASSWORD} | docker login -u \${DOCKER_HUB_USERNAME} --password-stdin"
                sh "docker push \${DOCKER_HUB_REPO}:latest"
            }
        }
    }
}
