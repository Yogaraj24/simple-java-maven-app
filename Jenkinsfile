// pipeline {
//     agent any
//     stages {
//         stage('Build') {
//             when{
//                 branch 'master'
//             }
//             steps {
//                 sh 'mvn package'
//             }
//         }
//         stage('Test') {
//           when{
//             branch 'test'
//           }
//             steps {
//                 sh 'mvn test'
//             }
//             post {
//                 always {
//                     junit 'target/surefire-reports/*.xml'
//                 }
//             }
//         }
//         stage('Deliver') {
//             steps {
//                 sh 'echo "Deploy code"'
//             }
//         }
//     }
// }

pipeline {
    agent any

    tools {
        maven 'insmaven'   // Maven version installed in Jenkins
        jdk 'insjava'           // JDK installed in Jenkins
    }

    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'master', url: 'https://github.com/Yogaraj24/simple-java-maven-app.git'
            }
        }

        stage('Build with Maven') {
            steps {
                sh 'mvn clean package'
            }
        }
    }

    post {
        success {
            echo "✅ Build Successful!"
        }
        failure {
            echo "❌ Build Failed!"
        }
    }
}

