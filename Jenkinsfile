pipeline {
    agent any
      environment {
        AWS_CREDENTIALS_ID = 'aws-credentials'
        REGION = 'us-east-1'
        REPOSITORY_URI = '081882787657.dkr.ecr.us-east-1.amazonaws.com/jenkins-push-image'
    }

    stages {
        stage('Start') {
            steps {
                echo 'Iniciando o build'
            }
        }
    }
}
