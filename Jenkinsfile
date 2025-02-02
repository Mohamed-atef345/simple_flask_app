pipeline {
    agent any

    stages {
        stage('build') {
            steps {
              scripts{
                  docker.withRegistry('https://index.docker.io/v1','docherhub_credentials') {
                    def testImage = docker.build("mohamedcloud/flaskapp_v:0.0.1") 
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
