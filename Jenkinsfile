// pipeline {
//   agent any
//   // tools { 
//   //   maven 'maven' 
//   //   // jdk 'jdk8' 
//   // }
//   options {
//     buildDiscarder (logRotator (numToKeepStr: '5'))
//   }
//   stages {
//     stage ('Scan') {
//       steps {
//         withSonarQubeEnv(installationName: 'sq1') {
//           sh 'mvn clean package sonar:sonar'
//         }
//       }
//     }
//   }
// }

pipeline { 
    agent any  
    stages { 
        stage('Build') { 
            steps { 
               echo 'This is a minimal pipeline.' 
            }
        }
    }
}
