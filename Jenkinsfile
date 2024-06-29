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
        stage('Install Node.js and npm') {
            steps {
                // Install Node.js and npm if not installed
                sh '''
                    if ! command -v node > /dev/null 2>&1; then
                        curl -sL https://deb.nodesource.com/setup_$NODE_VERSION | bash -
                        apt-get install -y nodejs
                    fi
                    # Ensure npm is installed and accessible
                    if ! command -v npm > /dev/null 2>&1; then
                        apt-get install -y npm
                    fi
                    echo "Node version:"
                    node -v
                    echo "NPM version:"
                    npm -v
                '''
            }
        }
        stage('Install Dependencies') {
            steps {
                // Change to the directory where package.json is located
                dir('my-nodejs-project') {  // Change this if your project directory name is different
                    sh 'npm install'
                }
            }
        }
        stage('Build') {
            steps {
                dir('my-nodejs-project') {  // Change this if your project directory name is different
                    sh 'echo "Building the project..."'
                }
            }
        }
        stage('Test') {
            steps {
                dir('my-nodejs-project') {  // Change this if your project directory name is different
                    sh 'npm test'
                }
            }
        }
        stage('Deploy') {
            steps {
                dir('my-nodejs-project') {  // Change this if your project directory name is different
                    sh 'echo "Deploying the application..."'
                }
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
