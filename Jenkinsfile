pipeline {
  agent any
  stages {
    stage('Set Original Workload') {
      when {
        branch 'deploy'
      }
      steps {
        echo 'Kubectl original online-boutique'
        sh '''gcloud config set project $PROJECT_ID
gcloud auth list
gcloud container clusters get-credentials alevz-demo-1-gke --zone asia-southeast2-a --project alevz-demo-1
kubectl get nodes
kubectl apply -f kubernetes-manifests.yaml'''
        sh 'cat Jenkinsfile'
      }
    }

    stage('Build Container and Push to GKE') {
      when {
        branch 'master'
      }
      steps {
        sh '''gcloud config set project $PROJECT_ID
gcloud auth list
gcloud container clusters get-credentials alevz-demo-1-gke --zone asia-southeast2-a --project alevz-demo-1
cat cloudbuild-jenkins.yaml
gcloud builds submit . --config cloudbuild-jenkins.yaml --substitutions=_LOCATION=$LOCATION,_CLUSTER=$CLUSTER'''
      }
    }

  }
  environment {
    LOCATION = 'asia-southeast2-a'
    CLUSTER = 'alevz-demo-1-gke'
    PROJECT_ID = 'alevz-demo-1'
  }
}