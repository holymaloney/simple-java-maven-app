pipeline {
  agent {
    docker {
      image 'maven:3-alpine'
      args '-v /var/lib/jenkins/.m2:/root/.m2:rw,z -e http_proxy=http://bf-proxy.osl.basefarm.net:8888 -e https_proxy=http://bf-proxy.osl.basefarm.net:8888 -e no_proxy=localhost,127.0.0.1,*.basefarm.net'
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
