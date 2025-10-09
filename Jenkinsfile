pipeline {
  agent any
  tools{
    maven 'Maven 3.9.11'
  }
  stages{
      stage("build"){
          steps{
              echo 'compaling sysfoo app...'
              sh 'mvn compile'
          }
      }
      stage("test"){
          steps{
              echo 'running test..'
              sh 'mvn clean test'
          }
      }
      stage("package"){
          steps{
              echo 'packaging the app'
              sh 'mvn package -DskipTests'
          }
      }
  }

  post{
    always{
        echo 'This pipeline is completed..'
    }
  }
}
