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
    stage('docker image') {
      
      steps {
       
       withDockerRegistry([ credentialsId: "Docker_hub", url: "https://index.docker.io/v1/" ]) {
       sh 'docker build -t devopstrainingschool/java-maven-jenkins . -f Dockerfile'
       sh 'docker push devopstrainingschool/java-maven-jenkins'
        
        }
       
        
     
         
      }
     }
      }
      }
