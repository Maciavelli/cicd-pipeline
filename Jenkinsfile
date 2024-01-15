pipeline {
  agent any
  tools { nodejs "nodejs" }

  stages {
    stage('Git checkout') {
      steps {
        git branch: 'main', url: 'https://github.com/Maciavelli/cicd-pipeline.git'
      }
    }

    stage('Build') {
      steps {
         sh 'npm install'
         sh 'chmod +x scripts/build.sh'
         sh 'scripts/build.sh'
      }
    }

  }
}
