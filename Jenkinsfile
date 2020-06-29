pipeline {
  agent { label "build && windows" }
  stages {
  stage('Nuget Restore') {
      steps {
        bat label: 'Nuget Restore', 
        script: '''
          nuget restore ".\\ConsoleApp1.sln"
          echo "Nuget Done Starting Msbuild *************"
        ''' 
      }
    }
	stage ('Build'){
		steps{
			bat "dir"
			bat "\"${tool 'msbuild_2017'}\"\\MSBuild.exe .\\ConsoleApp1.sln"
		}
	}
		
	stage ('Archive'){
		steps{
			archive 'sonarJenkinstest/bin/Release/**'   
		}
	}

  }
}