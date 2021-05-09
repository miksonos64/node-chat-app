pipeline {
	agent any
	
	tools {nodejs "node"}
	
	stages {
		stage('test') {
			steps {
				echo 'testowanie'
				sh 'npm install'
				sh 'npm run test'
			}
		}
	}
			post {

		failure{
			emailext attachLog: true,
			body: "${currentBuild.currentResult}: Job ${env.JOB_NAME} build ${env.BUILD_NUMBER}",
			to: 'iluzjionist99@gmail.com',
			subject: "test failed"
		}	
		success{
			echo 'udalo sie'
		}
	}
}
