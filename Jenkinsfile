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
                    export PATH=$PATH:/usr/local/bin
                    node -v
                    npm -v
                '''
            }
        }
        stage('Install Dependencies') {
            steps {
                // Install project dependencies
                sh '''
                    export PATH=$PATH:/usr/local/bin
                    npm install
                '''
            }
        }
        stage('Build') {
            steps {
                // Run build commands (if any)
                sh '''
                    export PATH=$PATH:/usr/local/bin
                    echo "Building the project..."
                '''
            }
        }
        stage('Test') {
            steps {
                // Run tests
                sh '''
                    export PATH=$PATH:/usr/local/bin
                    npm test
                '''
            }
        }
        stage('Deploy') {
            steps {
                // Deploy the application (if any)
                sh '''
                    export PATH=$PATH:/usr/local/bin
                    echo "Deploying the application..."
                '''
            }
        }
    }

    post {
        always {
            // Clean up actions
            sh '''
                export PATH=$PATH:/usr/local/bin
                echo "Cleaning up..."
            '''
        }
        success {
            // Actions on success
            sh '''
                export PATH=$PATH:/usr/local/bin
                echo "Pipeline completed successfully!"
            '''
        }
        failure {
            // Actions on failure
            sh '''
                export PATH=$PATH:/usr/local/bin
                echo "Pipeline failed!"
            '''
        }
    }
}
