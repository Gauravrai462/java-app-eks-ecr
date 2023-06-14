@Library('my-shared-library') _

pipeline {

 agent any
 
   stages{
         
        stage('Git Checkout'){
                 
            steps{
            gitcheckout(
                branch: "main",
                url: "https://github.com/Gauravrai462/mrdevops_java_app.git"
            )
            }
        }
      stage('mvn test'){
      
        steps{
          script{
          sh 'mvntest()'
          }
     }
    }
  }
}
