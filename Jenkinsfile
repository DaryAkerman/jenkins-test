pipeline {
    agent {
        kubernetes {
            yamlFile 'build-pod.yaml'
            defaultContainer 'ez-docker-helm-build'
        }
    }
    environment {
        DOCKER_IMAGE = "winterzone2/jenkins-test"
    }
    stages {
        stage("Checkout") {
            steps {
                checkout scm
            }
        }
        stage("Print Hello World") {
            when {
                not {
                    branch 'main'
                }
            }
            steps {
                sh "echo 'hello world'"
            }
        }
    }
}