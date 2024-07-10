pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                // Checkout the repository
                git 'https://github.com/talhasoomro/calculator.git'
            }
        }
        
        stage('Install dependencies') {
            steps {
                // Install Node.js dependencies
                sh 'npm install'
            }
        }
        
        stage('Build') {
            steps {
                // Build your Node.js application (if applicable)
                // Example: npm run build
                sh 'npm run build'
            }
        }
        
        stage('Test') {
            steps {
                // Run tests (if applicable)
                // Example: npm test
                sh 'npm test'
            }
        }
        
        stage('Deploy') {
            steps {
                // Deployment steps (if applicable)
                // Example: Deploying to a test server or pushing to Docker registry
                // Adjust this based on your deployment strategy
            }
        }
    }
    
    post {
        success {
            // Post-build actions (if any)
            echo 'Build succeeded!'
        }
        failure {
            // Post-build actions for failure (if any)
            echo 'Build failed!'
        }
    }
}
