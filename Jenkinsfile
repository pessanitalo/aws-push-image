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

    stages {
        stage('StartAuthenticate to ECR') {
            steps {
               script{
                     withCredentials([usernamePassword(credentialsId: "${AWS_CREDENTIALS_ID}", usernameVariable: 'AWS_ACCESS_KEY_ID', passwordVariable: 'AWS_SECRET_ACCESS_KEY')]) {
                        sh 'aws ecr get-login-password --region ${REGION} | docker login --username AWS --password-stdin ${REPOSITORY_URI}'
                   }
               }
            }
        }
    }
}
