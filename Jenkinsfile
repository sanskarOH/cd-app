pipeline {
    agent any

    tools {
        nodejs 'Node18'
    }

    environment {
        NETLIFY_AUTH_TOKEN = credentials('NETLIFY_AUTH_TOKEN')
        NETLIFY_SITE_ID = credentials('NETLIFY_SITE_ID')
    }

    stages {

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Build Project') {
            steps {
                sh 'npm run build'
            }
        }

        stage('Install Netlify CLI') {
            steps {
                sh 'npm install -g netlify-cli'
            }
        }

        stage('Deploy to Netlify') {
            steps {
                sh '''
                netlify deploy \
                --dir=dist \
                --prod \
                --site=$NETLIFY_SITE_ID \
                --auth=$NETLIFY_AUTH_TOKEN
                '''
            }
        }
    }
}