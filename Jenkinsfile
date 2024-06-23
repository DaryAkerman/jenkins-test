pipeline {
    agent {
        kubernetes {
            yamlFile "build-pod.yaml"
            defaultContainer "ez-docker-helm-build"
        }
    }
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
        stage("Push") {
            when {
                branch 'main'
            }
            steps {
                script {
                    docker.withRegistry('https://registry.hub.docker.com', 'docker-creds') {
                        sh "docker push winterzone2/jenkins-test:latest"
                    }
                }
            }
        }
    }
}
