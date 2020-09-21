pipeline {
	 agent any
	 stages {
		stage('Nuget Restore'){
			steps{
				bat "nuget restore ConsoleApp1.sln"
			}
		}
		stage('Sonar Analysis'){
			steps{
				bat "\"${tool 'sonar-msbuild'}\"\\SonarScanner.MSBuild.exe begin /k:\"testesonar\" /d:sonar.host.url=\"http://192.168.1.69:9000\" /d:sonar.login=\"admin\" /d:sonar.password=\"admin\""
				bat "\"${tool 'msbuild_2017'}\"MSBuild.exe TesteCsharp\\ConsoleApp1.sln /t:Rebuild"
				bat "\"${tool 'sonar-msbuild'}\"\\SonarScanner.MSBuild.exe end /d:sonar.login=\"admin\" /d:sonar.password=\"admin\""
				
			}
		}
		stage ('Archive'){
			steps{
				archiveArtifacts 'ConsoleApp1/bin/Debug/**'  
			}
		}
	}
}