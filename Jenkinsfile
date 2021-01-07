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
    environment {
            EMAIL_TO = 'andrzej.sierocinski@gmail.com'
        }
    post {
            failure {
                emailext body: 'Check console output at $BUILD_URL to view the results. \n\n ${CHANGES} \n\n -------------------------------------------------- \n${BUILD_LOG, maxLines=100, escapeHtml=false}',
                        to: "${EMAIL_TO}",
                        subject: 'Build failed in Jenkins: $PROJECT_NAME - #$BUILD_NUMBER'
            }
            unstable {
                emailext body: 'Check console output at $BUILD_URL to view the results. \n\n ${CHANGES} \n\n -------------------------------------------------- \n${BUILD_LOG, maxLines=100, escapeHtml=false}',
                        to: "${EMAIL_TO}",
                        subject: 'Unstable build in Jenkins: $PROJECT_NAME - #$BUILD_NUMBER'
            }
            changed {
                emailext body: 'Check console output at $BUILD_URL to view the results.',
                        to: "${EMAIL_TO}",
                        subject: 'Jenkins build is back to normal: $PROJECT_NAME - #$BUILD_NUMBER'
            }
       }
}
