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
                withMaven(maven: 'Mvn3') {
                    sh "mvn clean package"
                }
            }
        }
        stage('SCA-Scan') {
            steps {
                echo '---SCA AGENT SCAN---'
                withCredentials([ string(credentialsId: 'SCA_token', variable: 'SRCCLR_API_TOKEN')]) {
                    script {
                        if (isUnix() == true) {
                            sh "curl -sSL https://download.sourceclear.com/ci.sh | sh -s -- scan --ws 3OOuvgA"
                        }
                        else {
                            powershell '''
                            Set-ExecutionPolicy AllSigned -Scope Process -Force
                            $ProgressPreference = "silentlyContinue"
                            iex ((New-Object System.Net.WebClient).DownloadString('https://download.srcclr.com/ci.ps1'))
                            srcclr scan --ws 3OOuvgA
                            '''
                        }
                    }
                }
            }
        }
    }
}
