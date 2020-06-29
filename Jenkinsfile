pipeline {
  agent any
  stages {
	stage ('Build'){
		steps{
			bat "dir"
			bat "\"${tool 'msbuild_2017'}\"MSBuild.exe ${WORKSPACE}\\ConsoleApp1.csproj"
		}
	}
		
	stage ('Archive'){
		steps{
			archive 'sonarJenkinstest/bin/Release/**'   
		}
	}

  }
}