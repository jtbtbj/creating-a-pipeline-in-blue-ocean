pipeline {
  agent {
    docker {
      args '-e HTTP_PROXY=http://192.168.40.1:7897 -e HTTPS_PROXY=http://192.168.40.1:7897 -e NO_PROXY=localhost,127.0.0.1'
      image 'node:16-alpine'
    }
  }
  stages {
    stage('Install') {
      steps {
        sh '''
echo 'HTTP_PROXY: $HTTP_PROXY'
npm config delete registry
npm config delete proxy
npm config delete https-proxy
npm config set progress false
rm -f ./.npmrc
npm cache clean --force
NPM_CONFIG_REGISTRY=https://registry.npmjs.org/ npm install \
--no-audit --no-fund \
--fetch-retries=8 \
--fetch-retry-factor=2 \
--fetch-timeout=600000
'''
      }
    }
  }
}
