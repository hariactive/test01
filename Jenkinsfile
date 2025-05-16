pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/your-username/my-first-ci-cd.git'
            }
        }
        
        stage('Build') {
            steps {
                script {
                    // For Node.js:
                    sh 'npm install'
                    // For Python:
                    // sh 'pip install -r requirements.txt'
                }
            }
        }
        
        stage('Test') {
            steps {
                script {
                    // For Node.js:
                    sh 'npm test'
                    // For Python:
                    // sh 'python -m pytest test/'
                }
            }
        }
        
        stage('Deploy') {
            steps {
                script {
                    echo 'Deploying application...'
                    // Simple deployment step - would be more complex in real scenario
                    sh 'echo "Deployment completed"'
                }
            }
        }
    }
    
    post {
        always {
            echo 'Pipeline completed - cleaning up'
        }
        success {
            echo 'Pipeline succeeded!'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
}
