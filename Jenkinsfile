pipeline {
    agent any

    tools {
        nodejs 'Node18'
    }

    stages {

        stage('Install Dependencies'){
            steps{
                sh 'npm install'
            }    
        }
        stage('Build Project'){
            steps{
                sh 'npm run build'
        }

        }
        stage('Archive Project'){
            steps{
                sh archiveArtifacts artifacts: 'dist/**', fingerprint: true
            }
        }
        
    }
}