pipeline {
  agent any
  stages {
    stage('Git checkout') {
      steps {
        git(url: 'https://github.com/Maciavelli/cicd-pipeline.git', branch: 'main')
      }
    }

    stage('Build') {
      steps {
        sh 'sh \'scripts/build.sh\''
      }
    }

  }
}