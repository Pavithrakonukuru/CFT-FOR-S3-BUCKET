Pipeline {
    agent any
    stages {
        stage ('git checkout') {
            steps {
                sh 'export AWS_DEFAULT_REGION=us-west-2'
                sh 'aws cloudformation create-stack --stack-name iamuser --template-body file://s3.json --region us-west-2'
            }
        }
    }
}