
pipeline {
    agent any

    environment {
        GIT_URL = 'https://github.com/anand1025/demo-app.git'
        BRANCH_NAME = 'main'
    }

    stages {

        stage('Checkout') {
            steps {
                echo 'Downloading source code from GitHub'
                git branch: "${BRANCH_NAME}",
                    url: "${GIT_URL}"
            }
        }

        stage('Compile') {
            steps {
                echo 'Compiling the application'
                sh 'mvn clean compile'
            }
        }

        stage('Test') {
            steps {
                echo 'Running test cases'
                sh 'mvn test'
            }
        }

        stage('Build') {
            steps {
                echo 'Creating the application package'
                sh 'mvn package'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Application is ready for deployment'
            }
        }
    }

    post {
        success {
            echo 'Pipeline executed successfully!'
        }

        failure {
            echo 'Pipeline execution failed!'
        }
    }
}

