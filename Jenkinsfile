pipeline {
    agent any

    environment {
        PYTHON_HOME = 'C:\\Users\\Harini\\AppData\\Local\\Programs\\Python\\Python312'
        PATH = "${env.PYTHON_HOME};${env.PYTHON_HOME}\\Scripts;${env.PATH}"
    }

    stages {
        stage('Checkout') {
            steps {
                echo 'Cloning repository...'
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Building the application...'
                bat '"%PYTHON_HOME%\\python.exe" --version'
                bat '"%PYTHON_HOME%\\python.exe" build_script.py' // Replace with actual build script
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                bat '"%PYTHON_HOME%\\python.exe" test_script.py' // Replace with actual test script
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying the application...'
                bat '"%PYTHON_HOME%\\python.exe" deploy_script.py' // Replace with actual deployment script
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
