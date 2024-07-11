pipeline {
    agent any

    tools {
        nodejs "NodeJS"
    }

    environment {
        SUDO_PASSWORD = credentials('9c2d1268b6574edea83fcf9a1d32504a') // ID of the Jenkins credential
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
                // Ensure the application directory is correct
                dir('/path/to/your/application') {
                    // Start Node.js application in the background
                    sh 'nohup node app.js > app.log 2>&1 &'
                    sleep 10  // Optional: Wait for application to start (adjust as needed)

                    // Debugging steps
                    sh 'ps aux | grep node'  // Check if the node process is running
                    sh 'netstat -tuln | grep 5000'  // Check if port 5000 is being used
                    sh 'ls -l app.log'  // Check if app.log is created
                    sh 'cat app.log'  // Display contents of app.log
                    sh 'curl -I http://localhost:5000'  // Check if the application is accessible
                }
            }
        }

        stage('Deployment') {
            steps {
                // Reload Nginx using sudo with password provided via stdin
                sh 'echo $SUDO_PASSWORD | sudo -S systemctl reload nginx'
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
