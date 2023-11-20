pipeline {
  agent any
  tools { 
    maven 'Maven 3.3.9' 
    // jdk 'jdk8' 
  }
  options {
    buildDiscarder (logRotator (numToKeepStr: '5'))
  }
  stages {
    stage ('Scan') {
      steps {
        withSonarQubeEnv(installationName: 'sq1') {
          sh 'mvn clean package sonar:sonar'
        }
      }
    }
  }
}
