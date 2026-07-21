pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git url: 'https://github.com/YOUR_USERNAME/YOUR_REPO.git', branch: 'main'
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                sudo rm -rf /var/www/html/*
                sudo cp -r ./* /var/www/html/
                '''
            }
        }

        stage('Restart Nginx') {
            steps {
                sh 'sudo systemctl restart nginx'
            }
        }
    }

    post {
        success {
            echo 'Website Deployed Successfully!'
        }

        failure {
            echo 'Deployment Failed!'
        }
    }
}
