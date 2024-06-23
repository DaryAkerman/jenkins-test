pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Build') {
            steps {
                script {
                    sh "docker build -t winterzone2/jenkins-test:latest ."
                }
            }
        }
    }
}
