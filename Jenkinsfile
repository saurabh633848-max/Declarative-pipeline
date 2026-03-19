pipeline {
    agent any

    stages {
        stage('Clone GitHub Repo') {
            steps {
                git url: 'https://github.com/saurabh633848-max/Declarative-pipeline.git', branch: 'main'
            }
        }

        stage('Deploy to Nginx Default Path') {
            steps {
                echo 'Deploying website to Nginx default path...'
                sh '''
                    # Remove old files
                    sudo rm -rf /var/www/html/*
                    
                    # Copy new website files
                    sudo cp -r "${WORKSPACE}"/* /var/www/html/
                '''
            }
        }
    }

    post {
        success {
            echo '✅ Website deployed to Nginx default path (/var/www/html)'
        }
        failure {
            echo '❌ Deployment failed'
        }
    }
}
