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

			bat "\"${tool 'sonar-msbuild'}\"\\SonarScanner.MSBuild.exe begin /k:testSonarqube /d:sonar.host.url=http://192.168.1.253:9000 /d:sonar.login=1ec69f715c3bbba2837928c2dc265300ec2f6ac3"
			bat "\"${tool 'msbuild_2017'}\"MSBuild.exe TesteCsharp\\ConsoleApp1.sln /t:Rebuild"
			bat "\"${tool 'sonar-msbuild'}\"\\SonarScanner.MSBuild.exe end /d:sonar.login=1ec69f715c3bbba2837928c2dc265300ec2f6ac3"
		}
	}
	stage ('Archive'){
		steps{
			archive 'ConsoleApp1/bin/Debug/**'   
		}
	}

  }
}