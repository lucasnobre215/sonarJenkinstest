pipeline {
	 agent any
	 stages {

		stage('Sonar Analysis'){
			steps{
				bat "\"${tool 'sonar-msbuild'}\"\\SonarScanner.MSBuild.exe begin /k:\"testesonar\" /d:sonar.host.url=\"http://192.168.1.253:9000\" /d:sonar.login=\"admin\" /d:sonar.password=\"123\""
				bat "\"${tool 'msbuild_2017'}\"MSBuild.exe TesteCsharp\\ConsoleApp1.sln /t:Rebuild"
				bat "\"${tool 'sonar-msbuild'}\"\\SonarScanner.MSBuild.exe end /d:sonar.login=\"admin\" /d:sonar.password=\"123\""
				bat "\"${tool 'sonar-scanner'}\"\\sonar-scanner.bat -D\"sonar.host.url=http://192.168.1.253:9000\" -D\"sonar.login=861ba671ef165f11c5fd6a9d8d77077e2d20e33d\""
			}
		}

	}
}