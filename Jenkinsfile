pipeline {

  agent { label 'jenkins-docker-agent' }

  stages {

    stage('Checkout Source') {
      steps {
        git url:'https://github.com/ladung/playjenkins.git', branch:'test-deploy-dungla'
      }
    }

    stage('Deploy App') {
      steps {
        docker info
        sh 'ls -la'
	sh 'java -version'
        script {
          kubernetesDeploy(configs: "nginx.yaml", kubeconfigId: "kubeconfigdev")
        }
      }
    }

  }

}
