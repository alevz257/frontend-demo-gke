pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        echo 'Starting Build'
        apt-get install kubectl
        gcloud container clusters get-credentials alevz-demo-1-gke --zone asia-southeast2-a --project alevz-demo-1
        kubectl get nodes
      }
    }

  }
  environment {
    LOCATION = 'asia-southeast2-a'
    CLUSTER = 'alevz-demo-1-gke'
    PROJECT_ID = 'alevz-demo-1'
  }
}
