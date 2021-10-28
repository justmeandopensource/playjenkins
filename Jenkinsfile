pipeline {
  agent {
    kubernetes {
      //cloud 'kubernetes'
      containerTemplate {
        name 'maven'
        image 'maven:3.8.1-jdk-8'
        command 'sleep'
        args '99d'
      }
    }
  }
  stages {
    stage('Run maven') {
      steps {
        sh 'mvn -version'
      }
  }
}
}
