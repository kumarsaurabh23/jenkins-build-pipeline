// pipeline {
//     agent { docker { image 'maven:3.9.0-eclipse-temurin-11' } }
//     stages {
//         stage('build') {
//             steps {
//                 sh 'mvn --version'
//             }
//         }
//     }
// }
pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
