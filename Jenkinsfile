pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'echo "Building..."'
            }
        }
        stage('Test') {
            steps {
                sh 'echo "Testing..."'
            }
        }
        stage('Approval') {
            steps {
        
                mail to: 'sravanisoudampally@gmail.com',
                     subject: 'Approval needed for deployment',
                     body: 'Please approve the deployment by clicking this link: https://example.com/approve'
            }
        }
        stage('Deployment Approval') {
            steps {
                               input 'Proceed with deployment?'
            }
        }
        stage('Deploy') {
            steps {
                // Copy index.html from Jenkins server to Nginx server
                sh 'scp /path/to/index.html user@nginx-server:/path/to/nginx/html'
                echo 'Index.html copied to Nginx server'
            }
        }
    }
}

