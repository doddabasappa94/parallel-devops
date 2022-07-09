pipeline {
    agent any
    tools {
       maven 'maven-3.5.0'
    }
    stages{
        stage('checkout'){
         parallel {
          stage('main branch checkout') {
              steps{
              checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/doddabasappa94/parallel-devops.git']]])  
              sh 'mvn clean install'
              }
              }
          stage ('develop branch checkout') {
              steps{
              checkout([$class: 'GitSCM', branches: [[name: '*/develop']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/doddabasappa94/parallel-devops.git']]])
              sh 'mvn clean install' 
              }
          }
         }
        }
    }
}
