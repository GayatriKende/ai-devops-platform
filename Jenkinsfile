pipeline {
    agent any

    stages {

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
                sh 'docker build -t gayatrik2003/devops-ai .'
            }
        }

        stage('Push Docker Image') {
            steps {
                sh 'docker push gayatrik2003/devops-ai'
            }
        }

        stage('Deploy Container') {
            steps {
                sh '''
                docker stop devops || true
                docker rm devops || true
                docker run -d -p 5000:5000 --name devops gayatrik2003/devops-ai
                '''
            }
        }

    }
}
