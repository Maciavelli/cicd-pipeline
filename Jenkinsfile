pipeline {
  agent any
  stages {
    stage('Git checkout') {
      steps {
        git branch: 'main', url: 'https://github.com/Maciavelli/cicd-pipeline.git'
      }
    }

    stage('Build') {
      steps {
         sh 'scripts/build.sh'
      }
    }

  }
}
