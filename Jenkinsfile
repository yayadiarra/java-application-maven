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
    stage("sonar quality check"){
          
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
