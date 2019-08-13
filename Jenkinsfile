pipeline {

  environment {
    registry = "192.168.1.81:5000/justme/myweb"
  }

  agent any

  stages {

    stage('Cloning Git') {
      steps {
        git 'https://github.com/justmeandopensource/playjenkins.git'
      }
    }

    stage('Building image') {
      steps{
        script {
          docker.build registry + ":$BUILD_NUMBER"
        }
      }
    }

    stage('Deploy Image') {
      steps{
        script {
          docker.withRegistry( registry ) {
            dockerImage.push()
          }
        }
      }
    }

  }

}
