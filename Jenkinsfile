pipeline {
    agent any

    stages {
        stage('Clone GitHub Repo') {
            steps {
                git url: 'https://github.com/saurabh633848-max/Declarative-pipeline.git', branch: 'main'
            }
        }

        stage('Copy Files to /var/www') {
            steps {
                echo 'Copying files from Jenkins workspace to /var/www ...'
                sh '''
                    sudo rm -rf /var/www/*
                    sudo cp -r ${WORKSPACE}/* /var/www/
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
