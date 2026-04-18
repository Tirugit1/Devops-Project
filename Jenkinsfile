pipeline {
    agent any

    environment {
        PATH = "/usr/bin:/bin:/usr/local/bin"
    }

    stages {

        stage('Check Docker') {
            steps {
                sh 'echo "Checking Docker..."'
                sh 'which docker || true'
                sh 'docker --version'
            }
        }

        stage('Stop Old Container') {
            steps {
                sh 'docker rm -f devops-container || true'
            }
        }

        stage('Build Image') {
            steps {
                sh 'docker build -t devops-app .'
            }
        }

        stage('Run Container') {
            steps {
                sh 'docker run -d -p 5000:5000 --name devops-container devops-app'
            }
        }
    }
}