pipeline {
  agent any
  stages {
    stage('Build') {
      agent {
        docker {
          image 'google/cloud-sdk:latest'
          reuseNode true
        }
      }
      steps {
        echo 'Starting Build'
      }
    }

  }
  environment {
    LOCATION = 'asia-southeast2-a'
    CLUSTER = 'alevz-demo-1-gke'
    PROJECT_ID = 'alevz-demo-1'
  }
}
