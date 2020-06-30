pipeline {
  agent any
  stages {
	stage('Start Sonar Analysis'){
		steps{
		  bat "\"${tool 'sonar-scanner'}\"\\SonarQube.Scanner.MSBuild.exe begin /k:testSonarqube"
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
			bat "\"${tool 'sonar-scanner'}\"\\SonarQube.Scanner.MSBuild.exe end /k:testSonarqube"
		}
	}
	stage ('Archive'){
		steps{
			archive 'ConsoleApp1/bin/Debug/**'   
		}
	}

  }
}