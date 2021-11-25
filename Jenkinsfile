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
                echo '---BUILD---'
               // sh 'mvn clean package'
            }
        }
        stage('SCA-Scan') {
            steps {
                echo '---SCA AGENT SCAN---'
                sh "curl -sSL https://download.sourceclear.com/ci.sh | sh -s -- scan --ws 3OOuvgA"
            }
        }
        
    }
}
