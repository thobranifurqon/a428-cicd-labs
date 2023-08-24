pipeline {
    agent {
        docker {
            image 'node:16-buster-slim' 
            args '-p 3000:3000' 
        }
    }
    stages {
        stage('Build') { 
            steps {
                sh 'npm install' 
            }
        }
        stage('Test') {
            steps{
                sh './jenkins/scripts/test.sh' 

            }
        }
        stage ('Deploy') {
            steps{
                sh './jenkins/scripts/deliver.sh'
                timeout(time: 3, unit: 'HOURS'){
                    // input message: 'Sudah Selesai Menggunakan React App? (Klik "Proceed" untuk mengakhiri)'
                    sh './jenkins/scripts/kill.sh'
                }
                
                
            }
        }
    }
}