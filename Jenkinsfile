pipeline {
    agent any

    tools {
        nodejs 'nodeJS' // Change the version as needed
    }

    stages {
        stage('Git checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Maciavelli/cicd-pipeline.git'
            }
        }

        stage('Build') {
            steps {
                sh 'npm install'
                sh 'scripts/build.sh'
            }
        }
    }
}
