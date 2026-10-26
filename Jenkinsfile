pipeline {
  agent {
    docker {
      image 'node:16-alpine'
    }
  }
  stages {
    stage('Build') {
      steps {
        sh '''
npm config set progress false
npm config delete proxy
npm config delete https-proxy
npm config set registry https://registry.npmmirror.com/
npm config list
npm install --no-audit --no-fund --fetch-retries=5 --fetch-retry-factor=2
'''
      }
    }
  }
}
