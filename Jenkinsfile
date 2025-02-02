pipeline {
    agent any

    stages {
        stage('build') {
            steps {
                script {
                    docker.withRegistry('https://index.docker.io/v1/', 'dockerhub_credentials') {
                        def customImage = docker.build("mohamedcloud/flaskapp_v:0.0.1")
                        customImage.push()
                    }
                }
            }
        }
        
        stage('package') {
            steps {
                sh 'echo packaging....'
            }
        }

        stage('test') {
            agent {
                docker {
                    image 'ubuntu:latest'  // Define the Docker image for the test stage
                    label 'docker'         // Optional, if you need to specify a node with Docker installed
                }
            }
            steps {
                sh 'echo testing......'
            }
        }

        stage('deploy') {
            input {
                message "Do you want to run the deployment container?"
            }
            steps {
                sh 'docker run -d --name flaskapp -p 5555:5000 mohamedcloud/flaskapp_v:0.0.1'
            }
        }
    }
}
