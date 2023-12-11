pipeline {
  environment {
  registry = "anjalideshpande/demo"
  registryCredential = 'dockerhub_id'
  dockerImage = ''
}
agent any
stages {
        stage('Build image') 
        {
          steps{
            script {
                    dockerImage = docker.build registry + ":$BUILD_NUMBER"
                    }
                }
         }
         stage('Deploy the image') 
         {
            steps{
              script {
                  docker.withRegistry( '', registryCredential ) 
                      {
                        dockerImage.push()
                      }
                  }
                }
          }
//           stage('Cleaning up') {
//               steps{
//                   bat "docker rmi $registry:$BUILD_NUMBER"
//               }
//           }
  }
}
