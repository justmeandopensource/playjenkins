pipeline {

  options {
    ansiColor('xterm')
  }

  agent {
    kubernetes {
      yamlFile 'builder.yaml'
    }
  }

  stages {

    stage ('Pre Actions-Build Started') {
        steps {
            slackSend (
              color: '#F7A200' ,
              message: "Hey, your CI/CD trigger has *Started* \n*Trigger: * `${env.JOB_NAME}` #${env.BUILD_NUMBER}\n<`https://jenkins.cams7.ml/job/${env.JOB_NAME}/${env.BUILD_NUMBER}`|OPEN JENKINS BUILD>\n*GitHub: * ${GIT_BRANCH} >> <${GIT_URL}|Open Github>" 
            )
        }
    }


    stage('Kaniko Build & Push Image') {
      steps {
        container('kaniko') {
          script {
            sh '''
            /kaniko/executor --dockerfile `pwd`/Dockerfile \
                             --context `pwd` \
                             --destination=private.nexus.cams7.ml/myweb:${BUILD_NUMBER}
            '''
          }
        }
      }
    }

    stage('Deploy App to Kubernetes') {     
      steps {
        container('kubectl') {
          withCredentials([file(credentialsId: 'mykubeconfig', variable: 'KUBECONFIG')]) {
            sh 'sed -i "s/<TAG>/${BUILD_NUMBER}/" yamls/myweb.yaml'
            sh 'kubectl apply -n demo210827 -f yamls/myweb.yaml'
          }
        }
      }
    }
  
  }
}