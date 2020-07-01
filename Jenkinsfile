pipeline {
	 agent any
	 stages {

		stage('Sonar Analysis'){
			steps{
				bat "\"${tool 'sonar-msbuild'}\"\\SonarScanner.MSBuild.exe begin /k:\"testesonar\" /d:sonar.host.url=\"http://192.168.1.253:9000\" /d:sonar.login=\"admin\" /d:sonar.password=\"123\""
				bat "\"${tool 'msbuild_2017'}\"MSBuild.exe TesteCsharp\\ConsoleApp1.sln /t:Rebuild"
				bat "\"${tool 'sonar-msbuild'}\"\\SonarScanner.MSBuild.exe end"
			}
		}
		stage ('Archive'){
			steps{
				archiveArtifacts 'ConsoleApp1/bin/Debug/**'  
			}
		}
	}
}