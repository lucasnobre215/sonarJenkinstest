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
			bat "\"${tool 'msbuild_2017'}\"\\msbuild.exe .\\ConsoleApp1.sln "
		}
	}
		
	stage ('Archive'){
		steps{
			archive 'sonarJenkinstest/bin/Release/**'   
		}
	}

  }
}