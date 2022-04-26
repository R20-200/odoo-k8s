pipeline {


	agent any


stages {
  stage('checkout source') {
             steps{
                git url:'https://github.com/R20-200/odoo-k8s.git', branch:'main'
             }
  }

     stage('Déployer application sur K8s Cluster') {
      steps {
       
        echo "L'étape actuelle est deployement"
        kubernetesDeploy(
                                credentialsType: 'KubeConfig',
                                kubeConfig: [path: '/var/lib/jenkins/deploy-odoo/.kube/config'],
                                configs: 'deploy-odoo.yaml', kubeconfigId: 'kubernetes',
         )
      }   
    }
}
}
