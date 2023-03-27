pipeline {
    agent any
    environment {
        APP_NAME = 'react-devops'
        GIT_REPO = 'https://github.com/awuzi/react-devops'
        BUILD_DIR = 'build'
        DEPLOY_DIR = '/var/www/html'
        GITHUB_TOKEN_2 = credentials('github-token')
    }
    tools {
        nodejs "node"
    }
    stages {
        stage('Checkout') {
            steps {
                checkout([
                    $class: 'GitSCM',
                    branches: [[name: '*/staging']],
                    userRemoteConfigs: [[url: GIT_REPO]]
                ])
            }
        }
        stage('Check vars') {
            steps {
                sh 'echo "Hello World"'
                sh 'echo $GITHUB_USERNAME'
                sh 'echo $GITHUB_TOKEN'
            }
        }
        stage('Rebase') {
            steps {
                withCredentials([string(credentialsId: 'github-token', variable: 'GITHUB_TOKEN')]) {
                    sh 'echo $GITHUB_TOKEN'
                    sh "git config user.email 'jenkins@example.com'"
                    sh "git config user.name 'Jenkins Pipeline'"
                    sh 'git fetch --all'
                    sh "git checkout staging"
                    sh "git rebase origin/dev"
                    sh "git remote remove origin"
                    sh "git remote add origin https://awuzi:${GITHUB_TOKEN}@github.com/awuzi/react-devops.git"
                    sh "git push origin staging --force-with-lease"
                }
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
