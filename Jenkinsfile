pipeline {

  agent any

  stages {

    stage('Kaniko Build & Push Image') {
      agent {
        kubernetes {
          label 'kaniko-builder'
          defaultContainer 'builder'
          yamlFile 'builder.yaml'
        }
      }
      steps {
        script {
          sh '''
          /kaniko/executor --dockerfile `pwd`/Dockerfile \
                           --context `pwd` \
                           --destination=justmeandopensource/myweb:${BUILD_NUMBER}
          '''
        }
      }
    }

    stage('Deploy App to Kubernetes') {
      steps {
        script {
          kubernetesDeploy(configs: "myweb.yaml", 
                           kubeconfigId: "mykubeconfig", 
                           enableConfigSubstitution: true)
        }
      }
    }
  }
}