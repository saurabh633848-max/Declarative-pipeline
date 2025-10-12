pipeline {
    agent any

    environment {
        GIT_REPO = 'https://github.com/your-username/your-repo.git'
        ZIP_FILE = 'your-archive.zip'  // Change this to your zip file name
        TARGET_DIR = '/var/www/html'
    }

    stages {
        stage('Clone GitHub Repo') {
            steps {
                git url: "${env.GIT_REPO}"
            }
        }

        stage('Unzip Website Files') {
            steps {
                script {
                    sh "unzip -o ${env.ZIP_FILE} -d site"
                }
            }
        }

        stage('Copy Files to Nginx') {
            steps {
                script {
                    // Clean the target dir (optional)
                    sh "sudo rm -rf ${env.TARGET_DIR}/*"
                    
                    // Copy new files
                    sh "sudo cp -r site/* ${env.TARGET_DIR}/"
                }
            }
        }

        stage('Restart Nginx (Optional)') {
            steps {
                script {
                    sh "sudo systemctl restart nginx"
                }
            }
        }
    }

    post {
        success {
            echo 'Website deployed successfully!'
        }
        failure {
            echo 'Deployment failed.'
        }
    }
}
