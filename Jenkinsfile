pipeline {

  agent { label 'jenkins-agent' }

  stages {

    stage('Checkout Source') {
      steps {
        git url:'https://github.com/ladung/playjenkins.git', branch:'test-deploy-stage'
      }
    }

    stage('Deploy App') {
      steps {
        script {
	  sh 'ls -la'
          kubernetesDeploy(configs: "nginx.yaml", kubeconfigId: "kubeconfigdev")
        }
      }
    }

  }

}
