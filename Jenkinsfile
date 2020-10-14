pipeline {
  agent any
  stages {
    stage('Initialize') {
      steps {
        echo 'Hello'
	sh 'env'
        sh 'mvn --version'
      }
    }

    stage('Build') {
      steps {
        sh 'mvn -DskipTests install'
      }
    }

    stage('Test') {
      steps {
        sh 'mvn test'
      }
    }

    stage('Report') {
      steps {
        junit 'target/surefire-reports/*.xml'
      }
    }

  }
}
