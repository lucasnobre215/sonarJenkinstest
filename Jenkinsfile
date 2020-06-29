pipeline {
  agent any
  stages {
	stage ('Build'){
		steps{
			bat "\"${tool 'msbuild_2017'}\"\\MSBuild.exe ${WORKSPACE}\\ConsoleApp1.sln"
		}
	}
		
	stage ('Archive'){
		steps{
			archive 'sonarJenkinstest/bin/Release/**'   
		}
	}

  }
}