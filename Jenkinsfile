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
                sh '''
                    unzip -o project.zip -d .
                '''
            }
        }

        stage('Copy Index and Site Files') {
            steps {
                echo 'Copying website files from templatemo_597_neural_glass to /var/www/html...'
                sh '''
                    sudo cp -r templatemo_597_neural_glass/* /var/www/html/
                '''
            }
        }

        stage('Restart Nginx') {
            steps {
                echo 'Restarting Nginx...'
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
