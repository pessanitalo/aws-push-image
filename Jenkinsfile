pipeline {
    agent any
      environment {
        AWS_CREDENTIALS_ID = 'b8e7a213-f420-41c0-9c71-e81fc7c21842'
        REGION = 'us-east-1'
        REPOSITORY_URI = '081882787657.dkr.ecr.us-east-1.amazonaws.com/jenkins-push-image'
    }

    stages {
        stage('Start') {
            steps {
                echo 'Iniciando o build'
            }
        }
        stage('Debug Environment Variables') {
            steps {
                script {
                        echo "echo REGION=${REGION}"
                        echo "echo REPOSITORY_URI=${REPOSITORY_URI}"
                    }
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
                    withAWS(credentials: "${AWS_CREDENTIALS_ID}", region: "${REGION}") {
                        bat 'aws ecr get-login-password --region ${REGION} | docker login --username AWS --password-stdin ${REPOSITORY_URI}'
                    }
                }
            }
        }
    }
}
