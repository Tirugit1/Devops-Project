pipeline {
    agent any

    environment {
        PATH = "/usr/bin:/bin:/usr/local/bin:/usr/sbin"
    }

    stages {

        stage('Check Docker') {
            steps {
                sh 'echo PATH=$PATH'
                sh 'which docker || true'
                sh '/usr/bin/docker --version'
            }
        }

        stage('Stop Old Container') {
            steps {
                sh '/usr/bin/docker rm -f devops-container || true'
            }
        }

        stage('Build Image') {
            steps {
                sh '/usr/bin/docker build -t devops-app .'
            }
        }

        stage('Run Container') {
            steps {
                sh '/usr/bin/docker run -d -p 5000:5000 --name devops-container devops-app'
            }
        }
    }
}