pipeline {
    agent any

    tools {
        maven "maven"
    }
    environment{
        VERSION = "${env.BUILD_ID}"
        IMAGE_NAME = "devopstrainingschool/parker"
    }
    stages {
        stage('clean') {
            steps {
              
                
               
                sh "mvn  clean"

            }

            
        }
        stage('Build') {
            steps {
              
                
               
                sh "mvn  package"

            }

            
        }
       stage('docker image') {
      
      steps {
       
       withDockerRegistry([ credentialsId: "Docker_hub", url: "https://index.docker.io/v1/" ]) {
       sh 'docker build . -t $IMAGE_NAME:app1-$VERSION -f Dockerfile'
       sh 'docker tag $IMAGE_NAME:app1-$VERSION $IMAGE_NAME:$VERSION'
       sh 'docker push $IMAGE_NAME:app1-$VERSION'
       sh 'docker push $IMAGE_NAME:$VERSION'
        
        }
       
        
     
         
      }
     }
    }
}
