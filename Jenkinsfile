pipeline {
	agent any
	stages {
		stage("Start Grid") {
			steps{
				sh "docker-compose up -d hub chrome firefox"
			}
		}
		stage("Run Test") {
			steps{
				sh "docker-compose up search-module"
			}
		}
		// stage("Bring Grid down") {
		// 	steps {
		// 		sh "docker-compose down"
		// 	}
		// }
	}
	post{
		always{
			archiveArtifacts artifacts: 'output/**'
			sh "docker-compose down"
		}
	}
}