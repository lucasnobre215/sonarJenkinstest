pipeline {
  agent any
  stages {
	stage ('Build'){
		steps{
			bat "\"${tool 'msbuild_2017'}\"\\MSBuild.exe ConsoleApp1.sln"
		}
	}
		
	stage ('Archive'){
		steps{
			archive 'sonarJenkinstest/bin/Release/**'   
		}
	}

  }
}