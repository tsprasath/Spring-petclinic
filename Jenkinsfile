pipeline {
    agent {
         docker {
            image 'maven:3-jdk-8'
            }
    }
    stages {
          stage('Build and package') {
            agent { docker 'maven:3.5-alpine' }
            steps {
                sh 'mvn -B package -DskipTests'
                }
        }
stage('Unit Test') {
            steps {
                sh 'mvn test'
                sh 'mvn surefire-report:report'
            }
            post {
                always {
                  sh 'echo save unit test results'
                  junit '**/target/surefire-reports/TEST-*.xml'
                }
            }
        }
    }
}
