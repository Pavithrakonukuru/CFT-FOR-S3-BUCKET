pipeline {
    agent any

    parameters {
        string(name: 'BucketName', defaultValue: 'my-unique-bucket-name', description: 'Name for the S3 bucket')
    }

    environment {
        AWS_DEFAULT_REGION = 'us-west-2'
        STACK_NAME = 'my-s3-bucket-stack'
        TEMPLATE_FILE = 's3.yaml'
    }

    stages {
        stage('Deploy CloudFormation Stack') {
            steps {
                withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: 'Nani', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']]) {
                    script {
                        sh "aws cloudformation deploy --template-file $TEMPLATE_FILE --stack-name $STACK_NAME --parameter-overrides BucketName=${params.BucketName} --capabilities CAPABILITY_IAM"
                    }
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
