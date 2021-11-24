pipeline {
    agent any

    environment {
        def mvnHome = tool 'my-maven'
    }

    stages {
        stage('----Pull----') {
            steps {
                git 'https://github.com/gmdavef/example-java-maven'
            }
        }
        stage('----Build----') {
            steps {
                sh "${mvnHome}/bin/mvn clean package"
            }
        }
        stage('-----SCA-Agent-Scan-----') {
            steps {
                withCredentials([string(credentialsId: 'SRCCLR_API_TOKEN', variable: 'SRCCLR_API_TOKEN')]) {
                    sh '''
                        curl -sSL https://download.sourceclear.com/ci.sh | sh -s -- scan --ws 3OOuvgA --update-advisor
                    '''
                }
            }
        }
        
    }
}
