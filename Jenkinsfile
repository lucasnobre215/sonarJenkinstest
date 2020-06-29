pipeline {
  agent any
  stages {
    stage ('DIR'){
		steps{
			bat "dir"
		}
	}
	stage ('Build'){
		steps{
		bat "dir"
			bat "${tool 'msbuild_2017'}\\msbuild.exe ConsoleApp1\\ConsoleApp1.csproj -t:ConsoleApp1"
		}
	}
		
	stage ('Archive'){
		steps{
			archive 'sonarJenkinstest/bin/Release/**'   
		}
	}

  }
}