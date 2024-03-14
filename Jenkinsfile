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
        mail to: 'sravanisoudampally@gmail.com',
             subject: "Job '${JOB_NAME}' (${BUILD_NUMBER}) is waiting for input",
             body: "Please go to ${BUILD_URL} and verify the build"
        input (message: 'Proceed with deployment?', ok: 'Deploy')
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

