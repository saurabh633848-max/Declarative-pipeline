pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                // Jenkins automatically clones from repo (Jenkinsfile source)
                checkout scm
            }
        }

        stage('Deploy to Nginx') {
            steps {
                echo 'Deploying website to Nginx default path...'
                sh '''
                    # Clean old files
                   sh 'sudo rm -rf /var/www/html/index.nginx-debian.html'
                    
                    # Copy new files from workspace
                    cp -r * /var/www/html/
                '''
            }
        }
    }

    post {
        success {
            echo '✅ Website deployed successfully to /var/www/html'
        }
        failure {
            echo '❌ Deployment failed'
        }
    }
}
