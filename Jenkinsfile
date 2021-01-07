pipeline {
    agent any
    tools {nodejs "node"}
    stages {
        stage('Node') {
            steps {
                git url: 'https://github.com/AndrzejSierocinski/cypress-automation-framwork-finished.git'
                bat 'npm install'
                bat 'npm update'
                bat 'npm run %Script%'
            }
        }
    }
}
