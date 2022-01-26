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
				
				bat 'echo $DOCKERHUB_CREDENTIALS_PSW && docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}
	}

	post {
		always {
			bat 'docker logout'
		}
	}

}
