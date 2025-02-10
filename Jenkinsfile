pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                script {
                    echo "Cloning repository..."
                    checkout scm
                    sh 'pip install -r requirements.txt'
                }
            }
        }
        
        stage('Test') {
            steps {
                script {
                    echo "Running unit tests..."
                    def testResult = sh(script: 'python -m unittest test_app.py', returnStatus: true)
                    if (testResult != 0) {
                        error "Tests failed!"
                    }
                }
            }
        }
        
        stage('Deploy') {
            when {
                expression { currentBuild.result == null || currentBuild.result == 'SUCCESS' }
            }
            steps {
                script {
                    echo "Deployment Successful"
                }
            }
        }
    }
}
