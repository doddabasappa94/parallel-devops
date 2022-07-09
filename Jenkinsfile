pipeline {
    agent any
    stages{
        stage('checkout'){
         parallel {
          stage('main branch checkout') {
              steps{
              checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/doddabasappa94/parallel-devops.git']]])  
              }
              }
             stage('devops branch checkout') {
              steps{
              checkout([$class: 'GitSCM', branches: [[name: '*/develop']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/doddabasappa94/parallel-devops.git']]])  
              }
              }
         }
        }
         stage('Build'){
         parallel {
                    stage('Build docker image'){
            steps{
                script{
                    sh 'docker build -t doddabasappah/devops-app1 .'
                }
            }
        }
             
               stage('Build docker image'){
            steps{
                script{
                    sh 'docker build -t doddabasappah/devops-app2 .'
                }
            }
        }
         }
         }
        stage ('Push') {
            parallel{
            stage('Push image to Hub'){
             steps{
                script{
                   withCredentials([string(credentialsId: 'dockerhub-pwd', variable: 'dockerhubpwd')]) {
                   sh 'docker login -u doddabasappah -p ${dockerhubpwd}'
                     }
                   sh 'docker push doddabasappah/devops-app1'
                }
             }
            }
            stage('Push image to Hub'){
             steps{
                script{
                   withCredentials([string(credentialsId: 'dockerhub-pwd', variable: 'dockerhubpwd')]) {
                   sh 'docker login -u doddabasappah -p ${dockerhubpwd}'
                     }
                   sh 'docker push doddabasappah/devops-app2'
                }
             }
            }
         }
         }

    
    }
}
