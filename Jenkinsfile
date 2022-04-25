pipeline {
//      environment {
//	registryCredential = 'dockerhublogin'
//          }

	agent any


stages {
  stage('checkout source') {
             steps{
                git url:'https://github.com/R20-200/odoo-k8s.git', branch:'main'
             }
  }
  
//	    stage('Maven Install') {
//      agent {
//        docker {
//          image 'maven:3.5.0'
//        }
//      }
//      steps {
//        sh 'mvn clean install'
//      }
//    }
  //stage('Build image') {
  //  steps{
  //    script {
  //      dockerImage = docker.build dockerimagename
  //    }
  //   }
  //  }

 //   stage('Pushing Image') {
 //     environment {
 //              registryCredential = 'dockerhublogin'
 //          }
//      steps{
//        script {
//          docker.withRegistry( 'https://registry.hub.docker.com', registryCredential ) {
//            dockerImage.push("latest")
//          }
//        }
//      }
//    }
 
 
//		stage('Build image') {

//			steps {
//				sh 'docker build -t assc/odoo-container:latest .'
//			}
//		}


//		stage('Push image into docker hub') {
//
//			steps {
//        script {
//            docker.withRegistry( 'https://registry.hub.docker.com', registryCredential ) {
//            dockerImage.push("latest")
//	  }
//			}
//		}
//	}

//	post {
//		always {
//			sh 'docker logout'
//		}
//	}

    stage('Deploying App to Kubernetes') {
      steps {
        script {
          kubernetesDeploy(configs: "deploy-odoo.yaml", kubeconfigId: "kubernetes")
        }
      }
    }

  }

}
