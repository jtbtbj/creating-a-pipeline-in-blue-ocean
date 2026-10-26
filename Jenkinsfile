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
echo "HTTP_PROXY: $HTTP_PROXY"
# 删除项目目录里优先级最高的 .npmrc，防止劫持
rm -f ./.npmrc
# 清除npm用户层registry配置
npm config delete registry
npm config set progress false
# NPM_CONFIG_REGISTRY 优先级高于所有npmrc，锁定官方源
NPM_CONFIG_REGISTRY=https://registry.npmjs.org/ npm install --no-audit --no-fund --fetch-retries=5 --fetch-retry-factor=2
'''
      }
    }
  }
}
