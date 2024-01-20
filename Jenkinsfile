pipeline {
    agent any

    tools {
        nodejs 'nodeJS'
    }
    environment {
        DOCKER_REGISTRY_URL = 'docker.io/kuatishe'
        DOCKER_IMAGE_NAME = 'epam-ci-cd'
        DOCKER_IMAGE_TAG = 'latest'
        DOCKER_REGISTRY_CREDENTIALS = credentials('dockerhub_id')

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
                sh 'chmod +x scripts/build.sh'
                sh 'scripts/build.sh'
            }
        }
        stage('Test') {
            steps {
                script {
                    sh 'chmod +x scripts/test.sh'
                    sh 'scripts/test.sh'
                }
            }
        }
        
        stage('Build Image') {
            steps {
                script {
                    sh 'ls -lah /var/run/docker.sock '
                    sh 'docker build -t epam:v1 .'
                }
            }
        }
        
        stage('Docker Login and Push') {
            steps {
                script {
                    sh 'echo $DOCKER_REGISTRY_CREDENTIALS_PSW | docker login -u $DOCKER_REGISTRY_CREDENTIALS_USR --password-stdin docker.io'
                    sh "docker tag ${DOCKER_IMAGE_NAME}:${DOCKER_IMAGE_TAG} ${DOCKER_REGISTRY_URL}/${DOCKER_IMAGE_NAME}:${DOCKER_IMAGE_TAG}"
                    sh "docker push ${DOCKER_REGISTRY_URL}/${DOCKER_IMAGE_NAME}:${DOCKER_IMAGE_TAG}"
                    sh 'docker logout'
                }
            }
        }
    } 
}
