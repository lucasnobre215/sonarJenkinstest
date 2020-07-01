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
				bat "\"${tool 'sonar-msbuild'}\"\\SonarScanner.MSBuild.exe begin /k:testSonarqube /d:sonar.verbose=true /d:sonar.host.url=http://localhost:9000 /d:sonar.login=admin /d:sonar.password=123"
				bat "\"${tool 'msbuild_2017'}\"MSBuild.exe TesteCsharp\\ConsoleApp1.sln /t:Rebuild"
				bat "\"${tool 'sonar-msbuild'}\"\\SonarScanner.MSBuild.exe end /d:sonar.login=admin /d:sonar.password=123"
			}
		}
		stage ('Archive'){
			steps{
				archive 'ConsoleApp1/bin/Debug/**'  
			}
		}
	}
}