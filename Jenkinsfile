pipeline {
    agent any

    stages {
        stage('Clone GitHub Repo') {
            steps {
                git url: 'https://github.com/saurabh633848-max/Declarative-pipeline.git', branch: 'main'
            }
        }

        stage('Unzip Website Files') {
            steps {
                echo 'Unzipping project.zip...'
                // Unzip project.zip inside the workspace directory
                sh '''
                   unzip -o project.zip -d .
                '''
            }
        }

        stage('Copy Files to Nginx') {
            steps {
                echo 'Copying files to /var/www/html...'
                // Copy all unzipped files to nginx root
                sh '''
                   sudo cp -r * /var/www/html/
                '''
            }
        }

        stage('Restart Nginx (Optional)') {
            steps {
                echo 'Restarting Nginx...'
                // Restart nginx to apply changes
                sh '''
                   sudo systemctl restart nginx
                '''
            }
        }
    }

    post {
        failure {
            echo 'Deployment failed.'
        }
    }
}
