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
        powershell ':: Truncate the GIT_COMMIT to the first 7 characters set GIT_SHORT_COMMIT=%GIT_COMMIT:~0,7%  :: Set the version using Maven mvn versions:set -DnewVersion=%GIT_SHORT_COMMIT% mvn versions:commit'
        powershell 'mvn package -DskipTests'
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