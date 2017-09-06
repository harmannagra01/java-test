pipeline {
  agent any

  options {
    buildDiscarder(logRotator(numToKeepStr: '10', artifactNumToKeepStr: '1'))
  }

  stages {

    stage('Unit Tests') {
      steps {
        sh 'source ~/.bash_profile'
        sh 'ant -f test.xml -v'
        junit 'reports/result.xml'
      }
    }

    stage ('build') {
      steps {
        sh 'ant -f build.xml -v'
      }
    }
  }

  post {
    always {
      archiveArtifacts artifacts: 'dist/*.jar', fingerprint: true
    }
  }
}
