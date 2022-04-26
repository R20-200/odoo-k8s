pipeline {


	agent any


stages {
  stage('checkout source') {
             steps{
                git url:'https://github.com/med363/crud-users-tutorial.git', branch:'main'
             }
  }

    stage('Deploying App to Kubernetes') {
      steps {
        script {
          kubernetesDeploy(configs: "deployment.yml", kubeconfigId: "kubernetes")
        }
      }
    }

  }

}
        
