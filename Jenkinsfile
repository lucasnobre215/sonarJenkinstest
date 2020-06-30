pipeline {
  agent any
  stages {
	stage('Start Sonar Analysis'){
		steps{
		  bat "\"${tool 'sonar-scanner'}\"\\SonarScanner.MSBuild.exe begin /k:testSonarqube /d:sonar.host.url=http://192.168.1.253:9000 /d:sonar.login=be7afe423973616ec30aea28493b1bc6fa1ab613"
		}
	}
	
	stage ('Build'){
		steps{
			tool name: 'msbuild_2017', type: 'msbuild'
			bat "\"${tool 'msbuild_2017'}\"MSBuild.exe TesteCsharp\\ConsoleApp1.sln"
		}
	}
	stage('Stop Sonar Analysis'){
		steps{
			bat "\"${tool 'sonar-scanner'}\"\\SonarScanner.MSBuild.exe end /d:sonar.login=be7afe423973616ec30aea28493b1bc6fa1ab613"
		}
	}
	stage ('Archive'){
		steps{
			archive 'ConsoleApp1/bin/Debug/**'   
		}
	}

  }
}