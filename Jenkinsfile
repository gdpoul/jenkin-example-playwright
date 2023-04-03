pipeline {
  agent any
  stages {
     stage('build') {
            steps {
                script {
                   /* the return value gets caught and saved into the variable MY_CONTAINER */
                   MY_CONTAINER = bat(script: '@docker run -d -i mcr.microsoft.com/playwright:v1.32.0-focal', returnStdout: true).trim()
                   echo "mycontainer_id is ${MY_CONTAINER}"
                }
            }
      }
    stage('install playwright') {
      steps {
        script {
              bat "npm i -D @playwright/test"
              bat "npx playwright install"
        }
      }
    }
    stage('test') {
      steps{
        script {
        bat "npx playwright test"
        }
      }
    }
  }
}