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
                sh 'node app'  // Replace with your build command if applicable
            }
        }

        stage('Deployment') {
            steps {
                sh 'sudo systemctl reload nginx'  // Reload Nginx after deployment
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
