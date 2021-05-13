pipeline {

    agent any
    	tools{nodejs "node"}
	
    stages {
        stage('Build') {
            steps {
                echo 'Budowanko'
                sh 'npm install'
        }
            
        post {
         always {
            echo 'ended '
         }
         success {
            echo 'done'
            emailext attachLog: true,
                body: "${currentBuild.currentResult}: Job ${env.JOB_NAME} build ${env.BUILD_NUMBER}",
                to: 'iluzjionist99@gmail.com',
                subject: "logs success"
         }
         failure {
            echo 'error'
            emailext attachLog: true,
                body: "${currentBuild.currentResult}: Job ${env.JOB_NAME} build ${env.BUILD_NUMBER}",
                to: 'iluzjionist99@gmail.com',
                subject: "log error"
         }
     	 }
       }
       
        stage('Test') {
            steps {
                echo 'testowanie'
                sh 'npma run test'
            }
		
	post {
		always {
		    echo 'end'
		}
		success {
		    echo 'udalo sie'
		    emailext attachLog: true,
			body: "${currentBuild.currentResult}: Job ${env.JOB_NAME} build ${env.BUILD_NUMBER}",
			to: 'iluzjionist99@gmail.com',
			subject: "log success"
		}
		failure {
		    echo 'error'
		    emailext attachLog: true,
			body: "${currentBuild.currentResult}: Job ${env.JOB_NAME} build ${env.BUILD_NUMBER}",
			to: 'iluzjionist99@gmail.com',
			subject: "test failed"
		}
    	}
      }
    }
}
