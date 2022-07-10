pipeline {
  agent any
  tools {
  maven "maven"
  }
  stages {
    stage ('clean') {
      steps{
      sh "ls -al"
      }
      }
    stage ('build') {
      steps {
        sh ' mvn clean package'
      }
    }
      }
      }
