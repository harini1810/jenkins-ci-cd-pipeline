pipeline {
    agent any

    environment {
        GIT_HOME = 'C:\\Windows\\Git\\cmd\\git.exe'
        PYTHON_HOME = 'C:\\Users\\Harini\\AppData\\Local\\Programs\\Python\\Python312'
        PATH = "${PYTHON_HOME};${PYTHON_HOME}\\Scripts;${env.PATH}"
    }

    stages {
        stage('Build') {
            steps {
                echo 'Cloning GitHub repository...'
                bat '"%GIT_HOME%" clone https://github.com/harini1810/jenkins-ci-cd-pipeline'

                echo 'Installing dependencies...'
                bat 'cd jenkins-ci-cd-pipeline && "%PYTHON_HOME%\\python.exe" -m pip install -r requirements.txt'
            }
        }

        stage('Test') {
            steps {
                echo 'Running unit tests...'
                bat 'cd jenkins-ci-cd-pipeline && "%PYTHON_HOME%\\python.exe" -m pytest > test-results.log'
            }
        }

        stage('Deploy') {
            when {
                expression { return currentBuild.result == null || currentBuild.result == 'SUCCESS' }
            }
            steps {
                echo 'Deployment Successful!' // Replace this with actual deployment logic
            }
        }
    }

    post {
        success {
            echo 'Pipeline executed successfully!'
        }
        failure {
            echo 'Pipeline failed! Deployment skipped.'
        }
    }
}
