pipeline {
    agent any

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
    }
}