pipeline {
agent any
  stages {

    stage('Checkout Source') {
      steps {
        git 'https://github.com/jhasourav141/playjenkins.git'
      }
    }

    

    stage('Deploy App') {
      steps { 
          echo 'deploying the application'
          echo "deploying with ${my-kubeconfig}"
          bat '${my-kubeconfig}'
          
        }
    }  
    

 } 
}



      
