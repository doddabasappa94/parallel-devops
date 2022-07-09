pipeline {
    agent any
    stages{
      parallel main: {
        stage('Checkout'){
            steps{
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/doddabasappa94/parallel-devops.git']]])
                ##sh 'mvn clean install'
            }
        }
      }, develop: {
        stage('Build docker image'){
            steps{
              checkout([$class: 'GitSCM', branches: [[name: '*/develop']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/doddabasappa94/parallel-devops.git']]])
            }
        },
          failFast: true|false
      } 
    }
}
