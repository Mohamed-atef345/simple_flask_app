pipeline {
    agent any

    stages {
        stage('build') {
            steps {
              script {
                    docker.withRegistry('https://index.docker.io/v1','dockerhub_credentials') {
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
            steps {
                sh 'echo testing......'
            }
        }
    }
}
