pipeline {
    agent any

    environment {
        NODE_VERSION = '14.x'
    }

    stages {
        stage('Checkout') {
            steps {
                // Checkout the repository
                git branch: 'main', url: 'https://github.com/fal7w/jenkins-pipline.git'
            }
        }
        stage('Install Node.js') {
            steps {
                // Install Node.js version specified
                sh 'curl -sL https://deb.nodesource.com/setup_$NODE_VERSION | bash -'
                sh 'apt-get install -y nodejs'
            }
        }
        stage('Install Dependencies') {
            steps {
                // Install project dependencies
                sh 'npm install'
            }
        }
        stage('Build') {
            steps {
                // Run build commands (if any)
                echo 'Building the project...'
            }
        }
        stage('Test') {
            steps {
                // Run tests
                sh 'npm test'
            }
        }
        stage('Deploy') {
            steps {
                // Deploy the application (if any)
                echo 'Deploying the application...'
            }
        }
    }

    post {
        always {
            // Clean up actions
            echo 'Cleaning up...'
        }
        success {
            // Actions on success
            echo 'Pipeline completed successfully!'
        }
        failure {
            // Actions on failure
            echo 'Pipeline failed!'
        }
    }
}
