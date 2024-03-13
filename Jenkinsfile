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
        input 'Proceed with deployment?'
                mail to: 'sravanisoudampally@gmail.com',
                     subject: 'Approval needed for deployment',
                     body: 'Please approve the deployment by clicking this link: https://18.133.237.165:8080//approve'
            }
        }
       
        stage('Deploy') {
            steps {
                 def nginxServerUsername = 'ubuntu'
                    def nginxServerHost = '13.40.68.224'
                    def nginxServerPath = '/var/www/html'
                    def localFilePath = ''

                sh 'scp /path/to/index.html user@nginx-server:/path/to/nginx/html'
                echo 'Index.html copied to Nginx server'
            }
        }
    }
}

