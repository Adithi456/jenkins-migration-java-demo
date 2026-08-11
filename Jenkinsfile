pipeline {
    agent any

    environment {
        APP_NAME = 'java-demo'
    }

    stages {

        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Docker Build') {
            steps {
                sh 'docker build -t ${APP_NAME}:${BUILD_NUMBER} .'
            }
        }
    }

    post {
        success {
            echo 'Java build completed successfully'
        }

        failure {
            echo 'Java build failed'
        }
    }
}
