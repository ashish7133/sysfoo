pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        echo 'Compiling sysfoo app..'
        powershell 'mvn compile'
      }
    }

    stage('test') {
      steps {
        echo 'running unit tests..'
        powershell 'mvn clean test'
      }
    }

    stage('package') {
      steps {
        echo 'packaging the app..'
        powershell '''set GIT_SHORT_COMMIT=%GIT_COMMIT:~0,7%
        mvn versions:set -DnewVersion=%GIT_SHORT_COMMIT%
        mvn versions:commit
        '''

        archiveArtifacts '**/target/*.jar'
      }
    }

  }
  tools {
    maven 'Maven 3.8.6'
  }
  post {
    always {
      echo 'This pipeline is completed..'
    }

  }
}
