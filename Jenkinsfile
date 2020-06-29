pipeline {
  agent any
  stages {
	stage ('Build'){
		steps{
			bat "\"${tool 'msbuild_2017'}\"\\msbuild.exe ConsoleApp1.sln"
		}
	}
		
	stage ('Archive'){
		steps{
			archive 'sonarJenkinstest/bin/Release/**'   
		}
	}

  }
}