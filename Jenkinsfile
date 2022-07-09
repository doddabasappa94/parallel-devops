pipeline {
    agent any
      parallel main:{
          stage('checkout') {
              checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/doddabasappa94/parallel-devops.git']]])
          }
    }, develop:{
          stage ('checkout') {
              checkout([$class: 'GitSCM', branches: [[name: '*/develop']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/doddabasappa94/parallel-devops.git']]])
          }
    },
    failFast: true|false
}

