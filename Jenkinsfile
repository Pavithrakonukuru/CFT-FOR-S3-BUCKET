pipeline {
    agent any

    environment {
        AWS_DEFAULT_REGION = 'us-west-2'
        STACK_NAME = 'my-s3-bucket-stack'
        TEMPLATE_FILE = 's3.yaml'
    }

    stages {
        stage('Deploy CloudFormation Stack') {
            steps {
                script {
                    sh 'aws cloudformation deploy --template-file $TEMPLATE_FILE --stack-name $STACK_NAME --capabilities CAPABILITY_IAM'
                }
            }
        }
    }

    post {
        success {
            echo 'CloudFormation stack deployed successfully!'
        }
        failure {
            echo 'CloudFormation stack deployment failed!'
        }
    }
}
