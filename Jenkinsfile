pipeline {

  agent { label 'jenkins-docker-agent' }

  stages {
    stage('Checkout Source') {
      steps {
        git url:'https://github.com/ladung/playjenkins.git', branch:'test-deploy-dungla'
      }
    }
    stage('Pushing Image') {
      environment {
               registryCredential = 'dockerloginnexus'
           }
      steps{
        script {
          docker.withRegistry( 'https://nexus.api-connect.io', registryCredential )
        }
      }
    }

    stage('Deploy App') {
      steps {
        sh 'docker build -t a:b -f Dockerfile .'
        sh 'ls -la'
	sh 'java -version'
        script {
          kubernetesDeploy(configs: "nginx.yaml", kubeconfigId: "kubeconfigdev")
        }
      }
    }

  }

}
