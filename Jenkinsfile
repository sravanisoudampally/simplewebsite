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
        stage('Email Approval') {
            steps {
                // Send an email with an approval link
                script {
                    def approvalLink = 'http://18.133.237.165:8080/approve'
                    def approvalMessage = "Please click the following link to approve: ${approvalLink}"
                    // Use a service to send email, e.g., SMTP or a third-party service
                    // This is just a placeholder for demonstration
                    // Replace it with actual code to send email
                    sh "echo '${approvalMessage}' | mail -s 'Approval Required' sravanisoudampally@gmail.com"
                }
                // Wait for approval
                input(message: 'Proceed with deployment?', ok: 'Deploy')
            }
        }

        
       stage('Deploy') {
            steps {
                script {
                    def nginxServerUsername = 'ubuntu'
                    def nginxServerHost = '13.40.68.224'
                    def nginxServerPath = '/var/www/html'
                    def localFilePath = 'index.html'

                    // Use SCP to copy files to the Nginx server
                    sh "scp -r ${localFilePath} ${nginxServerUsername}@${nginxServerHost}:${nginxServerPath}"
                }
                }
    }
    }
}

