pipeline {
  agent { label "build && windows" }
  stages {
    stage('Clean Workspace'){
      steps {
        cleanWs()
      }
    }
        
    stage('Nuget Restore') {
      steps {
        bat label: 'Nuget Restore', 
        script: '''
          nuget restore "sonarJenkinstest\\ConsoleApp1.sln"
          echo "Nuget Done Starting Msbuild *************"
        ''' 
      }
    }

    stage('Build') {
      steps {
        script {
          //def msbuild = tool name: 'msbuild_2017', type: 'hudson.plugins.msbuild.MsBuildInstallation'
          tool name: 'msbuild_2017', type: 'msbuild'
          bat "\"${tool 'msbuild_2017'}\"\\msbuild.exe sonarJenkinstest\\ConsoleApp1.sln"
        }
      }
    }


  }
}