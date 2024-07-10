pipeline {
    agent any

    tools{
        nodejs "NodeJS"
    }
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
                sh 'node app'
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
