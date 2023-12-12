pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build and Push to DockerHub') {
            steps {
                script {
                    docker.withRegistry('https://index.docker.io/v1/', 'docker-registry-credentials') {
                        def dockerImage = docker.build('harshadazurunge/docker-web-application:latest')
                        dockerImage.push()
                    }
                }
            }
        }

        // Add other stages for deployment if needed
    }
}
