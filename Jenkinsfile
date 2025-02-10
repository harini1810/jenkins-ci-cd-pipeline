pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                script {
                    echo "Cloning repository..."
                    checkout scm
                }
            }
        }

        stage('Build') {
            steps {
                script {
                    bat 'echo Building the application...'
                    bat 'python --version' // Example: Check Python version
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    bat 'echo Running tests...'
                    bat 'pytest' // Ensure pytest is installed
                }
            }
        }

        stage('Deploy') {
            steps {
                script {
                    bat 'echo Deploying the application...'
                }
            }
        }
    }

    post {
        success {
            echo 'Pipeline executed successfully!'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
}
