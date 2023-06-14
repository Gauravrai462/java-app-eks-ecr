@Library('my-shared-library') _

pipeline {

 agent any
 
   stages{
         
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
  }
}
