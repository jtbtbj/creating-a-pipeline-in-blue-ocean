pipeline {
  agent {
    docker {
      args '-p 3000:3000 -e HTTP_PROXY=http://192.168.40.1:7897 -e HTTPS_PROXY=http://192.168.40.1:7897 -e NO_PROXY=localhost,127.0.0.1'
      image 'node:16-alpine'
    }

  }
  stages {
    stage('Build') {
      steps {
        sh '''echo $HTTP_PROXY
npm config set progress false
npm config delete proxy
npm config delete https-proxy
npm config set registry https://mirrors.cloud.tencent.com/npm/
npm config list
npm install --no-audit --no-fund --fetch-retries=5 --fetch-retry-factor=2
'''
      }
    }

  }
}