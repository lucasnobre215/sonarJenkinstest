pipeline {
  agent any
  stages {
	stage('Start Sonar Analysis'){
		steps{
		  bat "\"${tool 'sonar-scanner'}\"\\SonarScanner.MSBuild.exe begin /k:testSonarqube"
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
			bat "\"${tool 'sonar-scanner'}\"\\SonarScanner.MSBuild.exe end"
		}
	}
	stage ('Archive'){
		steps{
			archive 'ConsoleApp1/bin/Debug/**'   
		}
	}

  }
}