pipeline {
    agent any

    stages {
        stage('Set Working Directory') {
            steps {
                dir("${env.HOME}/project") {
                    script {
                        sh 'podman-compose down'
                        
                        sh 'podman-compose up --build -d'
                    }
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
