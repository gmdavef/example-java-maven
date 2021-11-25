pipeline {
    agent any

    stages {
        stage('----Pull----') {
            steps {
                git 'https://github.com/gmdavef/example-java-maven.git'
            }
        }
        stage('----Build----') {
            steps {
               // sh 'mvn clean package'
                echo 'This is a minimal pipeline.'
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
