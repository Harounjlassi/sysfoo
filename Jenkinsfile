pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        echo 'compaling sysfoo app...'
        sh 'mvn compile'
      }
    }

    stage('test') {
      steps {
        echo 'running test..'
        sh 'mvn clean test'
      }
    }

    stage('package') {
      steps {
        echo 'packaging the app'
        sh 'mvn package -DskipTests'
        sh '''# Truncate the GIT_COMMIT to the first 7 characters
GIT_SHORT_COMMIT=$(echo $GIT_COMMIT | cut -c 1-7)
# Set the version using Maven
mvn versions:set -DnewVersion="$GIT_SHORT_COMMIT"
mvn versions:commit'''
        archiveArtifacts '**/target/*.jar'
      }
    }

  }
  tools {
    maven 'Maven 3.9.11'
  }
  post {
    always {
      echo 'This pipeline is completed..'
    }

  }
}