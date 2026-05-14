pipeline {

    agent any

    stages {

        stage('Checkout Code') {
            steps {
                echo 'Fetching source code from GitHub...'
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t professional-website .'
            }
        }

        stage('Remove Old Container') {
            steps {
                bat 'docker rm -f professional-container || exit 0'
            }
        }

        stage('Deploy Website') {
            steps {
                bat 'docker run -d -p 8090:80 --name professional-container professional-website'
            }
        }

        stage('Verification') {
            steps {
                echo 'Deployment completed successfully!'
            }
        }
    }

    post {

        success {
            echo 'Pipeline executed successfully 🚀'
        }

        failure {
            echo 'Pipeline failed ❌'
        }
    }
}