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

// pipeline { 
//     agent any  
//     stages { 
//         stage('Build') { 
//             steps { 
//                echo 'This is a minimal pipeline.' 
//             }
//         }
//     }
// }

pipeline {
    agent any
    stages {
        stage('SCM') {
            steps {
                git url: 'https://github.com/foo/bar.git'
            }
        }
        stage('build && SonarQube analysis') {
            steps {
                withSonarQubeEnv('My SonarQube Server') {
                    // Optionally use a Maven environment you've configured already
                    withMaven(maven:'Maven 3.5') {
                        sh 'mvn clean package sonar:sonar'
                    }
                }
            }
        }
        stage("Quality Gate") {
            steps {
                timeout(time: 1, unit: 'HOURS') {
                    // Parameter indicates whether to set pipeline to UNSTABLE if Quality Gate fails
                    // true = set pipeline to UNSTABLE, false = don't
                    waitForQualityGate abortPipeline: true
                }
            }
        }
    }
}
