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
        script {
            def jenkinsUrl = 'http://18.133.237.165:8080/job/simplewebsite/16/input/Proceed%20or%20Abort/proceedEmpty?token=approval-d695c394-9f46-4b3c-838a-c28ffe3aa323'
            def approvalMessage = "Please click the following link to approve: ${jenkinsUrl}"
            
            // Send email using Email Extension Plugin
            emailext(
                subject: 'Approval Required',
                body: approvalMessage,
                to: 'sravanisoudampally@gmail.com'
            )
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

