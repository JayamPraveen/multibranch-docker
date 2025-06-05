pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'docker build -t image3 .'
            }
        }
        stage ("Tag") {
            steps {
                sh 'docker tag image3 praveenja/paytmmovie:1.0'
            }
        }
        stage ("Push") {
            steps {
                script{
                withDockerRegistry(credentialsId: 'docker-creds') {
                   sh 'docker push praveeja/paytmmovie:1.0'      
                  }
                }
            }
        }
        stage ("Deploy") {
            steps {
                sh 'docker run -itd --name movie-app -p 3333:80 praveeja/paytmmovie:1.0'
            }
        }
    }
}
