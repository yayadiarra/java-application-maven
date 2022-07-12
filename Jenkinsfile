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
    stage("sonar quality Test"){
          
            steps{
                script{
                    withSonarQubeEnv('sonarqube') {
                           
                            sh 'mvn clean package sonar:sonar'
                    }

                   

                }  
            }
        
       
}
        stage("Quality Gate"){
           steps {
               script {
        timeout(time: 1, unit: 'HOURS') { 
        def qg = waitForQualityGate() 
        if (qg.status != 'OK') {
             error "Pipeline aborted due to quality gate failure: ${qg.status}"
    }
  }
           }
           }
} 
      }
      }
