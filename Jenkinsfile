pipeline {
    agent any

    environment {
        APP_NAME = 'java-demo'
    }

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                bat 'mvn clean package'
            }
        }

        stage('Test') {
            steps {
                bat 'mvn test'
            }
        }

        stage('Docker Build') {
            steps {
                bat 'docker build -t %APP_NAME%:%BUILD_NUMBER% .'
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
