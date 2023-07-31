pipeline {
    agent any
    
    stages {
        stage('Install dependencies') {
            steps {
                sh 'npm install --global newman'
                sh 'npm install newman-reporter-html'
            }
        }
        
        stage('Run tests') {
            steps {
                script {
                    sh "npm install --global newman"
                    sh "npm install newman"
                    // Set up environment variables
                    def environmentFile = 'sage_sprint.postman_environment.json'
                    def collectionFile = 'postman_collection.json'
                   // def preRequestScriptFile = 'JWT_Pre_Request_Scripts.js'
                    
                    // Execute pre-request script
                   // sh "node ${preRequestScriptFile}"
                    
                    // Run test cases using Newman
                    sh "newman run ${collectionFile} -e ${environmentFile} --reporters cli,html"

                }
            }
        }
    }
}
