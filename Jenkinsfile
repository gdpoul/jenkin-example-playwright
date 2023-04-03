pipeline {
  agent any
  stages {
     stage('build') {
            steps {
                script {
                   bat '@docker run -d -i mcr.microsoft.com/playwright:v1.32.0-focal'
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