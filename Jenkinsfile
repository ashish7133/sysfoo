pipeline {
  agent any
  tools {
        maven 'Maven 3.8.6' 
  }
  stages{
      stage("build"){
          steps{
              echo 'Compiling sysfoo app..'
              powershell 'mvn compile'
          }
      }
      stage("test"){
          steps{
              echo 'running unit tests..'
              powershell 'mvn clean test'
          }
      }
      stage("package"){
          steps{
              echo 'packaging the app..'
              powershell 'mvn package -DskipTests'
          }
      }
  }

  post{
    always{
        echo 'This pipeline is completed..'
    }
  }
}
