pipeline {
    agent any

    environment {
        JENKINS_NODE_COOKIE = 'dontKillMe'
    }

    stages {
        stage('Stop Existing Containers') {
            steps {
                script {
                    def runningContainers = sh(script: 'podman ps -q', returnStdout: true).trim()
                    if (runningContainers) {
                        echo 'Stopping existing containers...'
                        sh 'podman-compose down'
                    } else {
                        echo 'No running containers to stop.'
                    }
                }
            }
        }
        stage('Build and Start New Containers') {
            steps {
                script {
                    echo 'Building and starting new containers...'
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
