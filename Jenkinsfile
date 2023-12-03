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


        stage('Deploy') {
            steps {
            // Using credentials to deploy - Example using SSH key credential
                withCredentials([usernamePassword(credentialsId: 'b5a9dd88-9275-4ae6-9390-0e271db98d71', passwordVariable: 'password', usernameVariable: 'user')]) {
                    bat """ docker build -t ivandamynov/student:1.0.0 .
                            docker login -u %user% --password %pass%
                            docker push ivandamynov/student:1.0.0
                        """
                    }
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
