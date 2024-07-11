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

        stage('Build') {
            steps {
                // Perform any build steps, if applicable
            }
        }

        stage('Deployment') {
            steps {
                // Optionally, restart or reload Nginx to apply new configuration
                sh 'sudo systemctl reload nginx'  // Adjust for your system

                // Optionally, notify deployment success
                echo 'Deployment completed!'
            }
        }
    }

    post {
        success {
            echo 'Build succeeded!'
            // Optionally, trigger deployment stage or notifications
        }
        failure {
            echo 'Build failed!'
            // Optionally, handle failure scenarios
        }
    }
}
