pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Checkout the code from your Git repository
                git 'https://github.com/your-repo/your-nodejs-app.git'
            }
        }
        stage('Install Dependencies') {
            steps {
                // Install Node.js dependencies
                sh 'npm install'
            }
        }
        stage('Run Tests') {
            steps {
                // Run the tests
                sh 'npm test'
            }
        }
        stage('Build') {
            steps {
                // Build the application (if applicable)
                sh 'npm run build'
            }
        }
        stage('Archive Artifacts') {
            steps {
                // Archive the build artifacts (if any)
                archiveArtifacts artifacts: '**/dist/**/*', allowEmptyArchive: true
            }
        }
    }
    
    post {
        always {
            // Clean up and notifications
            cleanWs()
        }
        success {
            echo 'Build and Tests succeeded!'
        }
        failure {
            echo 'Build or Tests failed!'
        }
    }
}
