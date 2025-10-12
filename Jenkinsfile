pipeline {
    agent any

    stages {
        stage('Clone GitHub Repo') {
            steps {
                git url: 'https://github.com/saurabh633848-max/Declarative-pipeline.git', branch: 'main'
            }
        }

        stage('Copy Files to Nginx Directory') {
            steps {
                echo 'Copying files to /var/www/html/...'
                sh 'sudo cp -r * /var/www/html/'
            }
        }

        stage('Restart Nginx') {
            steps {
                echo 'Restarting Nginx...'
                sh 'sudo systemctl restart nginx'
            }
        }
    }

    post {
        success {
            echo '✅ Deployment successful.'
        }
        failure {
            echo '❌ Deployment failed.'
        }
    }
}
