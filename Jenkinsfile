pipeline {
  agent any
  stages {
	
	stage ('Build'){
		steps{
			bat "dir"
			tool name: 'msbuild_2017', type: 'msbuild'
			bat "\"${tool 'msbuild_2017'}\"MSBuild.exe TesteCsharp\\ConsoleApp1.sln"
		}
	}
		
	stage ('Archive'){
		steps{
			archive 'sonarJenkinstest/bin/Release/**'   
		}
	}

  }
}