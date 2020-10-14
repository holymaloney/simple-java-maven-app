pipeline {
  agent {
    docker {
      image 'maven:3-alpine'
      args '-v /var/lib/jenkins/.m2:/root/.m2 -e http_proxy -e https_proxy -e no_proxy '
    }

  }
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
