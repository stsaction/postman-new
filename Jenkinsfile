pipeline {
    agent any

    stages {

        stage('Run tests') {
            steps {
                script {
                    // Set up environment variables (ensure files are present in the workspace)
                    def environmentFile = 'sage_sprint.postman_environment.json'
                    def collectionFile = 'Postman_Collection.json'
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
