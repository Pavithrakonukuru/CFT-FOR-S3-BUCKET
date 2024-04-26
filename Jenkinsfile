pipeline {
    agent any

    environment {
        AWS_DEFAULT_REGION = 'your-aws-region'
        STACK_NAME = 'my-s3-bucket-stack'
        TEMPLATE_FILE = 's3_bucket.yaml'
    }

    stages {
        stage('Deploy CloudFormation Stack') {
            steps {
                withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: 'Nani', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']]) {
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
