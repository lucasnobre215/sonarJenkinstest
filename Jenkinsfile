pipeline {
  agent any
  stages {
	stage ('Build'){
		steps{
			bat "dir"
			bat "\"${tool 'msbuild_2017'}\"MSBuild.exe ${WORKSPACE}\\ConsoleApp1\\ConsoleApp1.sln"
		}
	}
		
	stage ('Archive'){
		steps{
			archive 'sonarJenkinstest/bin/Release/**'   
		}
	}

  }
}