pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'docker build -t image1 .'
            }
        }
        stage ("Tag") {
            steps {
                sh 'docker tag image1 praveenja/paytmbank:1.0'
            }
        }
        stage ("Push") {
            steps {
                script{
                   withDockerRegistry(credentialsId: 'docker-creds') {
                     sh 'docker push praveenja/paytmbank:1.0'      
                     }
                 }
            }
        }
        stage ("Deploy") {
            steps {
                sh 'docker run -itd --name bank-app -p 1111:80 praveenja/paytmbank:1.0'
            }
        }
    }
}
