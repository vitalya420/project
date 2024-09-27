pipeline {
    agent any

    environment {
        JENKINS_NODE_COOKIE = 'dontKillMe'
    }

    stages {
        stage('Stop Existing Containers') {
            steps {
                script {
                    sh 'podman-compose down'
                }
            }
        }
        stage('Build and Start New Containers') {
            steps {
                script {
                    sh 'podman-compose up --build -d'
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
