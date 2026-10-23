pipeline {
  agent {
    docker {
      image 'node:6-alpine'
      args '-p 3000:3000 -e HTTP_PROXY=http://192.168.40.1:7897 -e HTTPS_PROXY=http://192.168.40.1:7897 -e NO_PROXY=localhost,127.0.0.1'
    }

  }
  stages {
    stage('Build') {
      steps {
        sh '''echo $HTTP_PROXY
npm config set proxy $HTTP_PROXY
npm config set https-proxy $HTTPS_PROXY
npm config list
npm install --no-audit --no-fund'''
      }
    }

  }
}