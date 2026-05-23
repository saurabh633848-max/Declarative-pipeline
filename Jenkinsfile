pipeline {
    agent any

    environment {
        SERVER_IP = "10.0.1.20"
        DEPLOY_PATH = "/var/www/html"
    }

    stages {

        stage('Checkout Code') {
            steps {
                echo 'Cloning GitHub repository...'

                git branch: 'main',
                url: 'https://github.com/saurabh633848-max/Declarative-pipeline.git'
            }
        }

        stage('Deploy Website to Nginx EC2') {
            steps {

                sshagent(credentials: ['nginx-server']) {

                    sh """
                    
                    echo "Removing old website files from Nginx server..."

                    ssh -o StrictHostKeyChecking=no ubuntu@$SERVER_IP '
                    
                    sudo rm -rf $DEPLOY_PATH/*
                    
                    '

                    echo "Copying new website files..."

                    scp -o StrictHostKeyChecking=no -r * ubuntu@$SERVER_IP:$DEPLOY_PATH/

                    echo "Restarting Nginx..."

                    ssh -o StrictHostKeyChecking=no ubuntu@$SERVER_IP '
                    
                    sudo systemctl restart nginx
                    
                    '

                    """
                }
            }
        }
    }

    post {

        success {
            echo '✅ Website deployed successfully to Nginx EC2'
        }

        failure {
            echo '❌ Deployment failed'
        }
    }
}
