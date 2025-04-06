pipeline {
    agent any

    stages {
        stage('Build Docker Image') {
            steps {
                script {
                    // Build the Docker image
                    sh 'docker build -t my-app .'
                }
            }
        }

        stage('Run Docker Container') {
            steps {
                script {
                    // Stop and remove the container if it already exists
                    sh '''
                    docker rm -f my-app-container || true
                    '''

                    // Run the Docker container
                    sh 'docker run -d --name my-app-container -p 8000:8000 my-app'
                }
            }
        }
    }

    post {
        always {
            // Clean up unused Docker images and containers (optional)
            sh 'docker system prune -f'
        }
    }
}
