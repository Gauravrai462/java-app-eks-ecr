@Library('my-shared-library') _

pipeline {

 agent any

 parameters{

    string(name: 'ImageName', description: "Docker Image name", defaultValue: 'javaapp')
    string(name: 'ImageTag', description: "Docker tag name", defaultValue: 'v1')
    string(name: 'DockerHubUser', description: "Docker Image name", defaultValue: 'raigaurav95')
 }
 
   stages{
    
         stage(clean){
        steps{
         cleanWs()
        }
      }
        stage('Git Checkout'){
                 
            steps{
            gitcheckout(
                branch: "main",
                url: "https://github.com/Gauravrai462/java-app-eks-ecr.git"
            )
            }
        }
   
    
      /*stage('Unit Test maven'){

            steps{
               script{
                   
                   mvntest()
               }
            }
        }
    
     stage('mvn initigration test'){

           steps{

             mvnIntigration()
           }
      
     }*/
    
    /*stage('Static Code Analysis') {
      environment {
        SONAR_URL = "http://172.17.0.1:9000"
      }
      steps {
        withSonarQubeEnv(installationName: 'Sonar', credentialsId: 'sonar') {
         sh 'mvn clean package sonar:sonar'
        //withSonarQubeEnv(credentialsId: 'sonar') {
         //sh 'mvn clean package sonar:sonar'
        //withCredentials([string(credentialsId: 'sonar', variable: 'SONAR_AUTH_TOKEN')]) 
        //sh 'mvn clean package sonar:sonar -Dsonar.login=$SONAR_AUTH_TOKEN -Dsonar.host.url=${SONAR_URL}'
        }
      }
    }
   

    stage('quality Gate'){

     steps{
      qualitygate()
     }
    }*/

   stage('Build'){

     steps{
      mavenBuild()
     }
    }

   stage('Docker Build'){

     steps{
        script{
            dockerBuild("${params.ImageName}", "${params.ImageTag}", "${params.DockerHubUser}")
        }
      } 
    }

  stage('Docker Scan'){
     steps{
        script{
         
         sh """   
           trivy image raigaurav95/javaapp:latest > scan.txt
           cat scan.txt
           """
        }
      } 
   }   


  stage('Docker Push'){

     steps{
        script{
            dockerPush("${params.ImageName}", "${params.ImageTag}", "${params.DockerHubUser}")
        }
      } 
    } 
    
 
  }
}
