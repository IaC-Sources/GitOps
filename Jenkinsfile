pipeline {
  agent any
  stages {   
    stage('git pull') {
      steps {
        // https://github.com/IaC-Sources/GitOps.git will replace by sed command before RUN
        git url: 'https://github.com/IaC-Sources/GitOps', branch: 'main'
      }
    }
    stage('k8s deploy'){
      steps {
        withKubeConfig([credentialsId: 'cp-k8s', serverUrl: 'https://192.168.1.10:6443']) {
          sh 'kubectl apply -f deployment.yaml'
        }
      }
    }
  }
}
