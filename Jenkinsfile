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
        script {
          kubernetesDeploy(configs: "testpod.yaml")
        }
      }
    }

  }

}
