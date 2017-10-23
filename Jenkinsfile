pipeline {
  agent {
    docker {
      image 'px4io/px4-dev-simulation:2017-09-26'
      args '--env=CCACHE_DISABLE=1 --env=CI=1'
    }

  }
  stages {
    stage('Build') {
      parallel {
        stage('posix_sitl_default') {
          steps {
            sh '''make distclean;
make posix_sitl_default'''
          }
        }
      }
    }
    stage('Test') {
      parallel {
        sh ```echo "Hello Jenkins test"```
      }
    }
  }
  environment {
    CI = '1'
    CCACHE_DISABLE = '1'
  }
}
