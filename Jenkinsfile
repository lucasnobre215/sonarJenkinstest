pipeline {
	 agent any
	 stages {

		stage('Sonar Analysis'){
			steps{
				bat "sonar-scanner.bat -D\"sonar.projectKey=testesonar\" -D\"sonar.sources=.\" -D\"sonar.host.url=http://192.168.1.253:9000\" -D\"sonar.login=861ba671ef165f11c5fd6a9d8d77077e2d20e33d\""
			}
		}

	}
}