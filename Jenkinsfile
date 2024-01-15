pipeline {
    agent any

    tools {
        nodejs '14' // Change the version as needed
    }

    stages {
        stage('Git checkout') {
            steps {
                git 'https://github.com/Maciavelli/cicd-pipeline.git'
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
