pipeline {
  agent {
    docker {
      args '-e HTTP_PROXY=http://192.168.40.1:7897 -e HTTPS_PROXY=http://192.168.40.1:7897 -e NO_PROXY=localhost,127.0.0.1'
      image 'node:16-alpine'
    }
  }
  stages {
    stage('Build') {
      steps {
        sh '''echo $HTTP_PROXY
npm config set progress false
# 下面两行注释掉，不要删除npm代理配置，让npm读取系统的代理环境变量
# npm config delete proxy
# npm config delete https-proxy
npm config set registry https://mirrors.cloud.tencent.com/npm/
npm config list
npm install --no-audit --no-fund --fetch-retries=5 --fetch-retry-factor=2
'''
      }
    }
  }
}
