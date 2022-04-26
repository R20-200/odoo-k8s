pipeline {


	agent any


stages {
  stage('checkout source') {
             steps{
                git url:'https://github.com/R20-200/odoo-k8s.git', branch:'main'
             }
  }

    stage('Deploying App to Kubernetes') {
      steps {
        script {
          kubernetesDeploy(configs: "deploy-odoo.yaml", kubeconfigId: "kubernetes")
        }
      }
    }

  }

}
        
