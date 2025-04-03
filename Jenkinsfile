pipeline {
    agent any
      environment {
        AWS_CREDENTIALS_ID = 'jenkins-credential'
        REGION = 'us-east-1'
        REPOSITORY_URI = '081882787657.dkr.ecr.us-east-1.amazonaws.com/jenkins-push-image'
    }

    stages {
        stage('Start') {
            steps {
                echo 'Iniciando o build'
            }
        }

        stage('Debug Login Command') {
            steps {
                script {
                    bat "aws ecr get-login-password --region ${REGION} > login-output.txt"
                    bat "type login-output.txt"
                }
            }
        }

        stage('Login no ECR') {
            steps {
                script {
                    withAWS(credentials: 'jenkins-credential', region: 'us-east-1') {
                        bat 'aws ecr get-login-password --region ${REGION} | docker login --username AWS --password-stdin ${REPOSITORY_URI}'
                    }
                }
            }
        }
    }
}
