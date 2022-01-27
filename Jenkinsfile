pipeline{

	agent any

	environment {
		DOCKERHUB_CREDENTIALS=credentials('reshu-dockerhub')
	}

	stages {
	    
	    stage('gitclone') {

			steps {
				git 'https://github.com/shazforiot/nodeapp_test.git'
			}
		}

		stage('Build') {

			steps {
				bat 'docker build -t thetips4you/nodeapp_test:latest .'
			}
		}

		stage('Login') {

			steps {
				bat 'docker login -u reshudocker -p docker123'
			}
		}

		stage('Push') {

			steps {
				
			
				bat 'docker tag thetips4you/nodeapp_test reshudocker/my-repo2'
				bat 'docker push reshudocker/my-repo2'
			}
		}
	}

	post {
		always {
			bat 'docker logout'
		}
	}

}
