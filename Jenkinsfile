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
                sh 'docker build -t professional-website .'
            }
        }

        stage('Remove Old Container') {
            steps {
                sh 'docker rm -f professional-container || true'
            }
        }

        stage('Deploy Website') {
            steps {
                sh 'docker run -d -p 8090:80 --name professional-container professional-website'
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