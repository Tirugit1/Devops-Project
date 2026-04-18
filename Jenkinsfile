pipeline {
    agent any

    environment {
        PATH = "/usr/bin:/bin:/usr/local/bin"
    }

    stages {
        stage('Build') {
            steps {
                sh 'docker --version'
                sh 'docker build -t devops-app .'
            }
        }

        stage('Run') {
            steps {
                sh 'docker run -d -p 5000:5000 devops-app'
            }
        }
    }
}