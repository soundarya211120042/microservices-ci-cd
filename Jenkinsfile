pipeline {
    agent any

    environment {
        DOCKER_COMPOSE_FILE = "docker-compose.yml"
    }

    stages {

        stage('Build Docker Images') {
            steps {
                script {
                    sh "docker-compose -f docker-compose.yml up --build -d"
                }
            }
        }

        stage('Verify Deployment') {
            steps {
                script {
                    // Simple check if containers are running
                    sh "docker-compose ps -a"
                }
            }
        }
    }

    post {
        always {
            echo "Pipeline run completed!"
        }
    }
}
