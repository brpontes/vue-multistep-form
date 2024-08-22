pipeline {
    agent any
    stages {
        withEnv(['PATH+NODE=~/.nvm/versions/node/v22.6.0/bin/node']) {
            stage('Check out') {
                steps {
                    checkout scm
                }
            }
            stage('Prepare') {
                steps {
                    sh 'npm install -g yarn'
                    sh 'yarn install'
                }
            }
            stage('Build') {
                steps {
                    sh 'yarn build'
                }
            }
            stage('Test') {
                steps {
                    echo 'Testing..'
                }
            }
            stage('Deploy') {
                steps {
                    echo 'Deploying....'
                }
            }
        }
    }
}
