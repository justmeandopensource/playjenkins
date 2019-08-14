pipeline {

  environment {
    registry = "10.95.65.195:5000/justme/myweb"
    dockerImage = ""
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
          dockerImage = docker.build registry + ":$BUILD_NUMBER"
        }
      }
    }

    stage('Deploy Image') {
      steps{
        script {
          docker.withRegistry( "" ) {
            dockerImage.push()
          }
        }
      }
    }

  }

}
