pipeline {
  agent any
  tools {
    maven "maven-stephanie"
  }
  stages {
    stage ('Maven Clean'){
      steps{
        sh 'mvn clean'
      }
    }
    stage ('Maven package') {
      steps{
        sh 'mvn package'
      }
    }
    
    stage ('Docker build and push'){
           steps{
             withDockerRegistry([ credentialsId: "Docker_creds", url: "https://index.docker.io/v1/" ]){
               sh 'docker build -t devopstrainingschool/java-maven-jenkins . -f Dockerfile'
               sh 'docker push devopstrainingschool/java-maven-jenkins'
             }
           }
           }
             
             
             

             
             
             
   
             
             
             
  }
}
  
