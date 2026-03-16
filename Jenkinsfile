pipeline {
    agent any

    environment {
        DOCKER_IMAGE = "gayatrik2003/devops-ai"
    }

    stages {

        stage('Checkout SCM') {
            steps {
                checkout scm
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'pip3 install -r requirements.txt'
            }
        }

        stage('Run Tests') {
            steps {
                sh 'python3 -m pytest'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh "docker build -t gayatrik2003/devops-ai ."
            }
        }

        stage('Docker Login') {
            steps {
                // Replace 'dockerhub-creds' with your Jenkins credentials ID
                withCredentials([usernamePassword(credentialsId: 'dockerhub-creds', usernameVariable: 'DOCKER_USER', passwordVariable: 'DOCKER_PASS')]) {
                    sh 'echo $DOCKER_PASS | docker login -u $DOCKER_USER --password-stdin'
                }
            }
        }

        stage('Push Docker Image') {
            steps {
                sh "docker push gayatrik2003/devops-ai"
            }
        }

        stage('Deploy Container') {
            steps {
                // Stops old container (if exists) and runs new one
                sh """
                docker stop devops-ai || true
                docker rm devops-ai || true
                docker run -d -p 5000:5000 --name devops gayatrik2003/devops-ai
                """
            }
        }

    }

    post {
        success {
            echo "Pipeline completed successfully!"
        }
        failure {
            echo "Pipeline failed! Check the logs."
        }
    }
}
