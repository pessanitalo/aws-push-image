pipeline {
    agent any
    stages {

        // stage('Debug Login Command') {
        //     steps {
        //         script {
        //             bat "aws ecr get-login-password --region ${REGION} > login-output.txt"
        //             bat "type login-output.txt"
        //         }
        //     }
        // }

        stage('Login no ECR') {
            steps {
                script {
                    withAWS(credentials: 'jenkins-credential', region: 'us-east-1') {
                        bat 'aws ecr get-login-password --region us-east-1 | docker login --username AWS --password-stdin 081882787657.dkr.ecr.us-east-1.amazonaws.com/jenkins-push-image'
                    }
                }
            }
        }
    }
}
