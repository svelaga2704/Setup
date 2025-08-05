pipeline {
    agent any

    environment {
        AWS_DEFAULT_REGION = 'us-east-2' // Change this if your bucket is in a different region
    }

    stages {
        stage('Preparation') {
            steps {
                echo 'Listing project files...'
                bat 'dir'
            }
        }

        stage('Upload to S3') {
            steps {
                withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', credentialsId: 'aws-access-key-id']]) {
                    bat '''
                        echo Uploading README.md to S3...
                        aws s3 cp README.md s3://git-jenkins-aws/README.md
                    '''
                }
            }
        }
    }
}
