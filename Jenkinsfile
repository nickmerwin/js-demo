pipeline {
  agent any
  stages {
    stage('Setup') {
      steps {
        sh 'npm install'
      }
    }
    stage('Build') {
      steps {
        sh 'npm test'
      }
    }
    stage('Coveralls') {
      steps {
        sh '''# cat ./coverage/lcov.info | ./node_modules/coveralls/bin/coveralls.js -v
printenv'''
      }
    }
  }
  environment {
    COVERALLS_SERVICE_NAME = 'jenkins-enterprise'
    COVERALLS_ENDPOINT = 'https://enterprise-demo-2.coveralls.io'
    COVERALLS_REPO_TOKEN = 'L1y26DsAcscI2AHIEgK5TiSdbS5UOSsIl'
    CI = 'true'
    CI_BRANCH = '$BRANCH_NAME'
    CI_BUILD_NUMBER = '$BUILD_NUMBER'
  }
}