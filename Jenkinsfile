pipeline {
  agent any

  stages {
     stage('build') {
            steps {
                script {
                   /* the return value gets caught and saved into the variable MY_CONTAINER */
                   MY_CONTAINER = bat(script: '@docker run -d -i mcr.microsoft.com/playwright:v1.32.0-focal', returnStdout: true).trim()
                   echo "mycontainer_id is ${MY_CONTAINER}"

                  //  /* python --version gets executed inside the Container */
                  //  bat "docker exec ${MY_CONTAINER} python --version "
                  //  /* the Container gets removed */
                  //  bat "docker rm -f ${MY_CONTAINER}"
                        }
                    }
                }
    stage('install playwright') {
      steps {
        sh '''
          npm i -D @playwright/test
          npx playwright install
        '''
      }
    }

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