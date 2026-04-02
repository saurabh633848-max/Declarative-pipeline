pipeline {
    agent any

    stages {

        stage('Checkout Code') {
            steps {
                echo 'Cloning repository...'
                git branch: 'main', url: 'https://github.com/saurabh633848-max/Declarative-pipeline.git'
            }
        }

        stage('Build') {
            steps {
                echo 'No build step required for static website...'
            }
        }

        stage('Deploy to Nginx') {
            steps {
                echo 'Deploying website to Nginx default path...'
                sh '''
                # Remove default nginx page
                rm -rf /var/www/html/*

                # Copy new website files
                cp -r * /var/www/html/
                '''
            }
        }
    }

    post {
        success {
            echo '✅ Deployment successful!'
        }
        failure {
            echo '❌ Deployment failed'
        }
    }
}
