pipeline {
  agent any
  stages {
	stage('Start Sonar Analysis'){
		steps{
			def sqScannerMsBuildHome = tool 'sonar-scanner'
			withSonarQubeEnv('My SonarQube Server') {
			  bat "${sqScannerMsBuildHome}\\SonarQube.Scanner.MSBuild.exe begin /k:testSonarqube"
			}
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
			def sqScannerMsBuildHome = tool 'sonar-scanner'
			withSonarQubeEnv('My SonarQube Server') {
				bat "${sqScannerMsBuildHome}\\SonarQube.Scanner.MSBuild.exe end"
			}
		}
	}
	stage ('Archive'){
		steps{
			archive 'ConsoleApp1/bin/Debug/**'   
		}
	}

  }
}