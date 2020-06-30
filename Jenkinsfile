pipeline {
	 agent any
	 stages {
		stage ('Build'){
			steps{
				tool name: 'msbuild_2017', type: 'msbuild'
				bat "\"${tool 'msbuild_2017'}\"MSBuild.exe TesteCsharp\\ConsoleApp1.sln"
			}
		}
		stage('Sonar Analysis'){
			steps{
				bat "\"${tool 'sonar-msbuild'}\"\\SonarScanner.MSBuild.exe begin /k:testSonarqube /d:sonar.host.url=http://192.168.1.253:9000 /d:sonar.login=bc811a8d370e2075fc6d95d8795d3a9c385e7bff"
				bat "\"${tool 'msbuild_2017'}\"MSBuild.exe TesteCsharp\\ConsoleApp1.sln /t:Rebuild"
				bat "\"${tool 'sonar-msbuild'}\"\\SonarScanner.MSBuild.exe end /d:sonar.login=bc811a8d370e2075fc6d95d8795d3a9c385e7bff"
			}
		}
		stage ('Archive'){
			steps{
				archive 'ConsoleApp1/bin/Debug/**'  
			}
		}
	}
}