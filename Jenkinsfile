pipeline {

  agent { label 'jenkins-docker-agent' }

  stages {
    stage('Checkout Source') {
      steps {
        git url:'https://github.com/ladung/playjenkins.git', branch:'test-deploy-dungla'
      }
    }
    stage('Docker build') {
     steps {
      container('jenkins-docker-agent') {
        sh 'docker version'
        sh 'docker build -t a:b -f Dockerfile .'
      }
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
