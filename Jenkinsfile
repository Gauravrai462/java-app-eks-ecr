@Library('my-shared-library') _

pipeline {

 agent any
 
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
   
    
      stage('Unit Test maven'){

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
      
     }
    
    stage('Static Code Analysis') {
      environment {
        SONAR_URL = "http://172.17.0.1:9000"
      }
      steps {
        withSonarQubeEnv(credentialsId: 'sonar', variable: 'SONAR_AUTH_TOKEN') {
         //sh 'mvn clean package sonar:sonar'
        //withCredentials([string(credentialsId: 'sonar', variable: 'SONAR_AUTH_TOKEN')]) {
        sh 'mvn clean package sonar:sonar -Dsonar.login=$SONAR_AUTH_TOKEN -Dsonar.host.url=${SONAR_URL}'
        }
      }
    }
   

    stage('quality Gate'){

     steps{
      qualitygate()
     }
    }
  }
}
