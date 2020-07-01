pipeline {
	 agent any
	 stages {

		stage('Sonar Analysis'){
			steps{
				bat "dotnet sonarscanner begin /d:sonar.login=admin /d:sonar.password=123 /k:\"AwesomeKey\""
				bat "dotnet build"
				bat "dotnet sonarscanner end /d:sonar.login=admin /d:sonar.password=123"
				
			}
		}

	}
}