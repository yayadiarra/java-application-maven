pipeline {
  agent any
  tools {
  maven "maven"
  }
  stages {
    stage ('clean') {
      steps{
      sh ' mvn clean'
      }
      }
    stage ('build & package the app') {
      steps {
        sh ' mvn package'
      }
    }
   
      }
      }
