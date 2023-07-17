pipeline {
  environment {
    dockerimagename = "pttzx/nodeapp"
    dockerImage = ""
  }
  properties([
    parameters([
        string(name: 'CompanyName', description: '', defaultValue: '', trim: true)
    ])
    ])
  agent any
  stages {

    stage('Checkout Source') {
      steps {
        git branch: 'main', url: 'https://github.com/WorkingDada/node-app.git'
      }
    }
    stage('Deploying App to Kubernetes') {
      steps {
        script {
          kubernetesDeploy(configs: "deploymentservice.yml", kubeconfigId: "kubernetes")
        }
      }
    }
  }
}
