pipeline{

	agent any

	environment {
		DOCKERHUB_CREDENTIALS=credentials('hanansalem88-dockerhub')
	}

	stages {

		stage('Build') {

			steps {
				sh 'docker build -t hanansalem88/runway-jenkies:latest .'
			}
		}

		stage('Login') {

			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}

		stage('Push') {

			steps {
				sh 'docker push hanansalem88/runway-jenkies:latest'
			}
		}
	}

	post {
		always {
			sh 'docker logout'
		}
	}

}