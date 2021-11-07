pipeline {

  agent { label 'jenkins-docker-agent' }

  stages {
    container('jenkins-docker-agent')
    stage('Checkout Source') {
      steps {
        git url:'https://github.com/ladung/playjenkins.git', branch:'test-deploy-dungla'
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
