pipeline {
    agent any

    tools {
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
        
        stage('Build and Run') {
            steps {
                // Start Node.js application in the background
                sh 'nohup node app.js > app.log 2>&1 &'
                
                // Wait for the application to start (adjust the sleep time as needed)
                script {
                    def appRunning = false
                    def maxAttempts = 12  // Adjust based on your needs
                    def attemptCount = 0
                    while (!appRunning && attemptCount < maxAttempts) {
                        try {
                            sh 'curl -sSf http://localhost:5000/ -o /dev/null'
                            appRunning = true
                        } catch (Exception e) {
                            echo "Waiting for application to start..."
                            sleep 10
                            attemptCount++
                        }
                    }
                    if (!appRunning) {
                        error "Application failed to start after ${maxAttempts * 10} seconds."
                    }
                }
            }
        }
    }
    
    post {
        success {
            // Perform post-build actions for success
            echo 'Build succeeded!'
            // Additional actions like testing or deployment can be added here
        }
        failure {
            // Perform post-build actions for failure
            echo 'Build failed!'
            // Additional actions for failure can be added here
        }
    }
}
