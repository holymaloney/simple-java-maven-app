pipeline {
  agent {
    docker {
      image 'maven:3-alpine'
      args '-v /root/.m2:/root/.m2'
    }

  }
  stages {
    stage('Initialize') {
      steps {
        echo 'Hello'
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