@Library('my-shared-library') _
pipeline {

 agent any
 
   stages{

     stage('checkout'){
       steps{
        gitCheckout(
        branch: "main",
        url: "https://github.com/Gauravrai462/java-app-eks-ecr.git" 
        )
         
        } 

  } 
 }
}
