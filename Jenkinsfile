pipeline {
    agent any

    tools {
        nodejs "NodeJS"
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/talhasoomro/calculator.git'
            }
        }

        stage('Install dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Start Application') {
            steps {
                // Start Node.js application in the background
                sh 'nohup node app > app.log 2>&1 &'
                sleep 10  // Optional: Wait for application to start (adjust as needed)
            }
        }

        stage('Deployment') {
            steps {
                sh 'systemctl reload nginx'  // Reload Nginx after deployment
                echo 'Deployment completed!'
            }
        }
    }

    post {
        success {
            echo 'Build succeeded!'
            // Optionally, trigger notifications or further actions
        }
        failure {
            echo 'Build failed!'
            // Optionally, handle failure scenarios
        }
    }
}
