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
      }
    }

    stage('Build') {
      steps {
        sh '''echo `mvn --version`
mvn -DskipTests install'''
      }
    }

  }
}