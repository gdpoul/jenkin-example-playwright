pipeline {
  agent { 
    docker { 
      image 'docker run -v C:/Users/ganes/.jenkins/workspace/Playwright-Typescript:/app -w /app mcr.microsoft.com/playwright:v1.32.0-focal'
    } 
  }
  stages {
    stage('install playwright') {
      steps {
        sh '''
          npm i -D @playwright/test
          npx playwright install
        '''
      }
    }
    // stage('help') {
    //   steps {
    //     sh 'npx playwright test --help'
    //   }
    // }
    stage('test') {
      steps {
        sh '''
          npx playwright test --list
          npx playwright test
        '''
      }
    }
  }
}