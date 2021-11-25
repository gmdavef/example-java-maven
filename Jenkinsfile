pipeline {
    agent any

    stages {
        stage('Pull') {
            steps {
                echo '---PULL---'
                git 'https://github.com/gmdavef/example-java-maven.git'
            }
        }
        stage('Build') {
            steps {
               // sh 'mvn clean package'
                echo '---BUILD---'
            }
        }
        stage('SCA-Scan') {
            steps {
                echo '---SCA AGENT SCAN---'
               // withCredentials([string(credentialsId: 'SRCCLR_API_TOKEN', variable: 'SRCCLR_API_TOKEN')]) {
                    script {
                        sh "curl -sSL https://download.sourceclear.com/ci.sh | sh"
                    }
               // }
            }
        }
        
    }
}
