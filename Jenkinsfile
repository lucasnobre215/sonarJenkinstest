pipeline {
  agent any
  stages {
	stage('Start Sonar Analysis'){
		steps{
			bat "SonarScanner.MSBuild.exe begin /k:\"testSonarqube" /d:sonar.host.url=\"http://192.168.1.253:9000\" /d:sonar.login=\"1493d0ad94e6c003487b4bf15f03cdcf8d61948c\""
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
			bat "SonarScanner.MSBuild.exe end -d:sonar.login=\"1493d0ad94e6c003487b4bf15f03cdcf8d61948c\""
		}
	}
	stage ('Archive'){
		steps{
			archive 'ConsoleApp1/bin/Debug/**'   
		}
	}

  }
}