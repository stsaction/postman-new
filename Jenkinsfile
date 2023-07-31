pipeline {
    agent any

    stages {
        stage('Install dependencies') {
            steps {
                // Install Newman and Newman HTML reporter without using sudo
                sh 'sudo npm install --global newman newman-reporter-html'
            }
        }

        stage('Run tests') {
            steps {
                script {
                    // Set up environment variables (ensure files are present in the workspace)
                    def environmentFile = 'sage_sprint.postman_environment.json'
                    def collectionFile = 'postman_collection.json'
                    // def preRequestScriptFile = 'JWT_Pre_Request_Scripts.js'

                    // Execute pre-request script (if needed)
                    // sh "node ${preRequestScriptFile}"

                    // Run test cases using Newman
                    sh "newman run ${collectionFile} -e ${environmentFile} --reporters cli,html"
                }
            }
        }
    }
}
