env.DOCKER_REGISTRY = 'rizaleko'
env.DOCKER_IMAGE_NAME = 'landing'
pipeline {
    agent any
    stages {
        
        stage('Git Pull from Github') {            
            steps {
                sh('sed -i "s/tag/$BUILD_NUMBER/g" index.html')
            }
        }
        stage('Build Docker Image') {
            steps {
                sh "docker build --build-arg APP_NAME=$DOCKER_IMAGE_NAME -t $DOCKER_REGISTRY/$DOCKER_IMAGE_NAME:$BUILD_NUMBER ."   
            }
        }        
    }
}
