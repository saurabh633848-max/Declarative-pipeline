pipeline {
    agent any

    stages {
        stage('Clone GitHub Repo') {
            steps {
                git url: 'https://github.com/saurabh633848-max/Declarative-pipeline.git', branch: 'main'
            }
        }

        stage('Copy Files to Nginx Root') {
            steps {
                echo 'Copying files from Jenkins workspace to /usr/share/nginx/html...'
                sh '''
                    # Remove old files from Nginx root
                    sudo rm -rf /usr/share/nginx/html/*
                    
                    # Copy new build files
                    sudo cp -r "${WORKSPACE}"/* /usr/share/nginx/html/
                '''
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
