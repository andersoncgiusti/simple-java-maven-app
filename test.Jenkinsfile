pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'mvn -B -DskipTests clean package'
      }
    }
    stage('Test') {
      steps {
        sh 'mvn test'
      }
      post {
        always {
          junit 'target/surefire-reports/*.xml'
        }
      }
    }
    stage('Delivery') {
      steps {
        sh './jenkins/scripts/delivery.sh'
      }
    }
    stage('Complete') {
      steps {
        echo 'Pipeline completed successfully!'
      }
    }
  }
}
