pipeline {
  agent any
  stages {
	stage('Checkout'){
      steps {
        checkout([$class: 'GitSCM', 
        branches: [[name: '*/master']], 
        doGenerateSubmoduleConfigurations: false, 
        extensions: [], 
        submoduleCfg: [], 
        userRemoteConfigs: [[url: 'https://github.com/ismail0352/Packer-Terraform-Jenkins.git']]])

      }
    }
    
    stage('Nuget Restore') {
      steps {
        bat label: 'Nuget Restore', 
        script: '''
          nuget restore "PrimeDotnet\\prime-dotnet.sln"
          echo "Nuget Done Starting Msbuild *************"
        ''' 
      }
    }

    stage('Build') {
      steps {
        script {
          //def msbuild = tool name: 'msbuild_2017', type: 'hudson.plugins.msbuild.MsBuildInstallation'
          tool name: 'msbuild_2017', type: 'msbuild'
		  bat "dir"
          bat "\"${tool 'msbuild_2017'}\"msbuild.exe PrimeDotnet\\prime-dotnet.sln"
        }
      }
    }
		
	stage ('Archive'){
		steps{
			archive 'sonarJenkinstest/bin/Release/**'   
		}
	}

  }
}