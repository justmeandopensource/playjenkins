podTemplate(containers: [
    containerTemplate(name: 'maven', image: 'maven:3.8.1-jdk-8', command: 'sleep', args: '99d'),
    containerTemplate(name: 'golang', image: 'golang:1.16.5', command: 'sleep', args: '99d')
])
    node(POD_LABEL) {
        stage('Get a Maven project') {
            git url:'https://github.com/ladung/playjenkins.git', branch:'test-deploy-stage'
            container('maven') {
                stage('Build a Maven project') {
                    sh 'echo "helloooooooooooooooooooooooooooooooooooooo!!!!!!"'
                }
            }
        }

