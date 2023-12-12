pipeline {
    agent any

    triggers {
        pollSCM('* * * * *')  // Poll every 5 minutes (adjust as needed)
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build and Test') {
            steps {
                script {
                    // Build Docker image
                    docker.build('ci-cd-example')
                }
            }
        }

        stage('Push to Docker Registry') {
            steps {
                script {
                    // Push Docker image to a registry (adjust registry URL and credentials)
                    docker.withRegistry('https://hub.docker.com/', 'docker-registry-credentials') {
                        docker.image('ci-cd-example').push()
                    }
                }
            }
        }

        // Add other stages for deployment if needed
    }
}
