pipeline {
    agent any

    triggers {
        pollSCM('H/5 * * * *') // Poll SCM every 5 minutes
    }

    stages {
        stage('Checkout Code') {
            steps {
                // Checkout your source code (assuming you have it in a version control system)
                checkout scm
            }
        }

        stage('Build and Push Docker Image') {
            steps {
                script {
                    // Build the Docker image
                    def dockerImage = docker.build('sabababa/maven-app:v1')

                    // Push the Docker image to Dockerhub
                    docker.withRegistry('https://registry.hub.docker.com', 'dockerhub_credentials') {
                        dockerImage.push()
                    }
                }
            }
        }

        stage('Deploy') {
            steps {
                // Deploy your Docker container (e.g., run it on a server or orchestrator)
                // Example: Run the container on the host
                sh 'docker run -d -p 8080:80 sabababa/maven-app:v1'
            }
        }
    }
}
