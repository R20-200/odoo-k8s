pipeline{

	agent any


	environment {

		DOCKERHUB_CREDENTIALS=credentials('assc2022')

		REGISTRY_ADDRESS = "https://hub.docker.com/repository/docker/assc2022/odoo"

	}

	stages {

		stage('Login and setup') {

			steps {

	         sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'

			}
		}

	stage('Build and push ') {

			steps {

         		 sh "chmod +x -R ${env.WORKSPACE}"

    		     sh './build.sh'
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
        
