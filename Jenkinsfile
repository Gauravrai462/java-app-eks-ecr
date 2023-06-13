@Library('my-shared-library') _

pipeline {

 agent any
 
   stages{
         
        stage('Git Checkout'){
                 
            steps{
            gitcheckout(
                branch: "main",
                url: "https://github.com/vikash-kumar01/mrdevops_java_app.git"
            )
            }
        }
  }
}
