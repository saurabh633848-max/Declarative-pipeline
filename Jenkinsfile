pipeline {
    agent any

    stages {
        stage('Clone GitHub Repo') {
            steps {
                git url: 'https://github.com/saurabh633848-max/Declarative-pipeline.git'
            }
        }

        stage('Unzip Website Files') {
            steps {
                echo 'Unzipping...'
                // Add actual unzip logic here
            }
        }

        stage('Copy Files to Nginx') {
            steps {
                echo 'Copying files to Nginx...'
                // Add your copy logic here
            }
        }

        stage('Restart Nginx (Optional)') {
            steps {
                echo 'Restarting Nginx...'
                // Add restart command here if needed
            }
        }
    }

    post {
        failure {
            echo 'Deployment failed.'
        }
    }
}
