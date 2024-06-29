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
        stage('Check Node.js and npm Installation') {
            steps {
                // Check if Node.js and npm are installed
                script {
                    def nodeInstalled = sh(script: 'command -v node', returnStatus: true) == 0
                    def npmInstalled = sh(script: 'command -v npm', returnStatus: true) == 0

                    if (!nodeInstalled || !npmInstalled) {
                        // Install Node.js and npm if not installed
                        sh '''
                            curl -sL https://deb.nodesource.com/setup_$NODE_VERSION | bash -
                            apt-get install -y nodejs
                        '''
                    } else {
                        // Print versions if installed
                        sh 'node -v'
                        sh 'npm -v'
                    }
                }
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
