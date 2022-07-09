pipeline {
    agent any
    stages{
        stage('checkout')
         parallel {
          stage('main branch checkout') {
              steps{
              checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/doddabasappa94/parallel-devops.git']]])  
              }
              }
          stage ('develop branch checkout') {
              steps{
              checkout([$class: 'GitSCM', branches: [[name: '*/develop']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/doddabasappa94/parallel-devops.git']]])
                }
          }
         }
    }
}

