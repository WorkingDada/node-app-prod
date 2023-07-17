pipeline {
  environment {
    dockerimagename = "pttzx/nodeapp"
    dockerImage = ""
  }
  agent any
  properties([
    parameters([
        string(name: 'Version', description: '', defaultValue: '', trim: true)
    ])
  ])
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
