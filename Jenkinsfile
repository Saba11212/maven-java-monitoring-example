pipeline {
    agent any
    
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

                    // Push the Docker image to a registry
                    dockerImage.push()
                }
            }
        }

        stage('Deploy') {
            steps {
                // Deploy your Docker container (e.g., run it on a server or orchestrator)
                // Example: Run the container on the host
                sh 'docker run -d -p 8081:80 sabababa/maven-app:v1'
            }
        }
    }
}
