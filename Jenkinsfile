pipeline {
  agent any
  stages {
    stage ('Build'){
		steps{
			
			bat "\"${tool 'msbuild_2017'}\" ConsoleApp1.sln /p:Configuration=Release /p:Platform=\"Any CPU\" /p:ProductVersion=1.0.0.${env.BUILD_NUMBER}"
		}
	}
		
	stage ('Archive'){
		steps{
			archive 'sonarJenkinstest/bin/Release/**'   
		}
	}

  }
}