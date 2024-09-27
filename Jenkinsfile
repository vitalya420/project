pipeline {
    agent any

    stages {
        stage('Stop Existing Containers') {
            steps {
                script {
                    // Stop and remove existing containers
                    sh 'podman-compose -f /path/to/your/docker-compose.yml down'
                }
            }
        }
        stage('Build and Start New Containers') {
            steps {
                script {
                    // Build and start new containers
                    sh 'podman-compose -f /path/to/your/docker-compose.yml up --build -d'
                }
            }
        }
    }
    post {
        always {
            echo 'Pipeline completed.'
        }
        success {
            echo 'Containers started successfully!'
        }
        failure {
            echo 'There was an issue starting the containers.'
        }
    }
}
