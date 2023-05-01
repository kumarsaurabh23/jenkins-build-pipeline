// pipeline {
//     agent any

//     stages {
//         stage('Build') {
//             steps {
//                 echo 'Building..'
//             }
//         }
//         stage('Test') {
//             steps {
//                 echo 'Testing..'
//             }
//         }
//         stage('Deploy') {
//             steps {
//                 echo 'Deploying....'
//             }
//         }
//     }
// }
pipeline {
    agent { docker { image 'maven:3.9.0-eclipse-temurin-11' } }
    stages {
        stage('Build') {
            steps {
                sh 'mvn package'
            }
        }
        stage('Test') {
            when {
              expression {
                isBuildSuccessful() == true 
              }
            }
            steps {
                sh 'mvn test'
//                 junit '**/target/*.xml'
            }
        }
        stage('Archive') {
            when {
              expression {
                isBuildSuccessful() == true 
              }
            }
            steps {
                archiveArtifacts artifacts: '**/target/*.jar', fingerprint: true
            }
        }
    }
}

Boolean isBuildSuccessful() {
    return currentBuild.result == null || currentBuild.result == 'SUCCESS'
}
