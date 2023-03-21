pipeline {
    agent any
    environment {
        APP_NAME = 'react-devops'
        GIT_REPO = 'https://github.com/awuzi/react-devops'
        BUILD_DIR = 'build'
        DEPLOY_DIR = '/var/www/html'
    }
    tools {
        nodejs "node"
    }
    stages {
        stage('Checkout') {
            steps {
                checkout([
                    $class: 'GitSCM',
                    branches: [[name: '*/main']],
                    userRemoteConfigs: [[url: GIT_REPO]]
                ])
            }
        }
        stage('Build') {
            steps {
                sh 'npm install'
                sh 'npm run build'
            }
        }
        stage('Store Build Folder') {
            steps {
                sh 'mkdir -p builds'
                sh 'cp -r dist builds/${BUILD_NUMBER}'
            }
        }
    }
}
