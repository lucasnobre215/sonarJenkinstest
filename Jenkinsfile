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
			bat "\"${tool 'msbuild_2017'}\"\\msbuild.exe .\\ConsoleApp1\\ConsoleApp1.csproj"
		}
	}
		
	stage ('Archive'){
		steps{
			archive 'sonarJenkinstest/bin/Release/**'   
		}
	}

  }
}