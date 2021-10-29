pipeline {

  agent { label 'jenkins-agent' }

  stages {

    stage('Checkout Source') {
      steps {
        git url:'https://github.com/ladung/playjenkins.git', branch:'test-deploy-dungla'
      }
    }

    stage('Deploy App') {
      steps {
        sh 'ls -la'
	sh 'java -version'
        script {
          kubernetesDeploy(configs: "nginx.yaml", kubeconfigId: "kubeconfigdev")
        }
      }
    }

  }

}
