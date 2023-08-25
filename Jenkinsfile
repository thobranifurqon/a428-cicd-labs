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
        stage('Manual Approval'){
            steps{
                input message: 'Lanjutkan ke tahap Deploy? (klik "Proceed" untuk lanjut ke tahap Deploy)'
            }
        }
        stage ('Deploy') {
            steps{
                sh './jenkins/scripts/deliver.sh'
                // input message: 'Sudah Selesai Menggunakan React App? (Klik "Proceed" untuk mengakhiri)'
                sh 'sleep 60'
                // sh './jenkins/scripts/kill.sh'
                
                
                
            }
        }
    }
}