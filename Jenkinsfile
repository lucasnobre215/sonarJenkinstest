pipeline {
  agent any
  stages {
    stage ('Build'){
		steps{
			ls
			bat "\"${tool 'msbuild_2017'}\"\\msbuild.exe ConsoleApp1.sln /p:Configuration=Release /p:Platform=\"Any CPU\" /p:ProductVersion=1.0.0.${env.BUILD_NUMBER}"
		}
	}
		
	stage ('Archive'){
		steps{
			archive 'sonarJenkinstest/bin/Release/**'   
		}
	}

  }
}