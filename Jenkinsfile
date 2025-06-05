pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'docker build -t image2 .'
            }
        }
        stage ("Tag") {
            steps {
                sh 'docker tag image2 praveenja/paytmbus:1.0'
            }
        }
        stage ("Push") {
            steps {
                script{
                withDockerRegistry(credentialsId: 'docker-creds') {
                   sh 'docker push praveenja/paytmbus:1.0'      
                  }
                }
            }
        }
        stage ("Deploy") {
            steps {
                sh 'docker run -itd --name bus-app -p 2222:80 praveenja/paytmbus:1.0'
            }
        }
    }
}
