pipeline {
    agent any
    stages {

        stage('Checkout') {
            steps {
                // Checkout code from a Git repository
                checkout scm
            }
        }

        stage('NPM Install') {
            steps {
                bat "npm install"
            }
        }
        
        stage('Run intergration tests') {
            steps {
                bat "npm run test"
                // Your test commands here
            }
        }
    }
    post {
        success {
            echo 'Pipeline successful! Yay!'
            // Actions to perform when the pipeline succeeds
        }
        failure {
            echo 'Pipeline failed! Oh no!'
            // Actions to perform when the pipeline fails
        }
    }
}
