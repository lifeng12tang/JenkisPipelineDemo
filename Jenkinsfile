pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                echo 'Hello World'
            }
        }
        stage('Build') {
            steps {
                echo 'Buliding stage'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying stage'
                withCredentials([[
                    $class: 'AmazonWebServicesCredentialsBinding',
                    credentialsId: 'MyAWS',
                    accessKeyVariable: 'AWS_ACCESS_KEY_ID',
                    secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']]){
                        sh(script: 'aws s3 cp /ProgramData/Jenkins/.jenkins/workspace/BuildJob/index.html S3://tang-jenkins-test')
            }
        }
        stage('Test') {
            steps {
                echo 'Testing stage'
            }
        }
        stage('Release') {
            steps {
                echo 'Releasing stage'
            }
        }
    }
}
