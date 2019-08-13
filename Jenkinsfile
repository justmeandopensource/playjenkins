pipeline {

  environment {
    registry = "10.95.65.195:5000/justme/myweb"
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
          docker.withRegistry( '' ) {
            dockerImage.push()
          }
        }
      }
    }

  }

}
