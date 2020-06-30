pipeline {
  agent any
  stages {
	stage('Start Sonar Analysis'){
		steps{
		  bat "\"${tool 'sonar-msbuild'}\"\\SonarScanner.MSBuild.exe begin /k:testSonarqube /d:sonar.host.url=http://192.168.1.253:9000 /d:sonar.login=c2daae71b8641df2a9115e832e796fa7adbfa111"
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
			bat "\"${tool 'sonar-msbuild'}\"\\SonarScanner.MSBuild.exe end /d:sonar.login=c2daae71b8641df2a9115e832e796fa7adbfa111"
		}
	}
	stage ('Archive'){
		steps{
			archive 'ConsoleApp1/bin/Debug/**'   
		}
	}

  }
}