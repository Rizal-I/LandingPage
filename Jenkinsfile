env.DOCKER_REGISTRY = 'rizaleko'
env.DOCKER_IMAGE_NAME = 'landing'
pipeline {
    agent any
    stages {        
<<<<<<< HEAD
        stage('build') {
            steps {
                sh('sed -i "s/tag/$BUILD_NUMBER/g" index.html')
                }
            }
        stage('docker build') {
            steps {
                sh "docker build --build-arg APP_NAME=$DOCKER_IMAGE_NAME -t $DOCKER_REGISTRY/$DOCKER_IMAGE_NAME:$BUILD_NUMBER ."
                }
           }
        stage('Docker push') {
            steps {                
                sh "docker push $DOCKER_REGISTRY/$DOCKER_IMAGE_NAME:$BUILD_NUMBER"
                }
           }
        stage('tagging') {
            steps {
                sh('sed -i "s/tag/$BUILD_NUMBER/g" landing.yml')
                }
           }
        stage('locate namespace') {
            steps {
                sh('sed -i "s/default/production/g" landing.yml')
                }
           }
        stage('add domain') {
            steps {
                sh('sed -i "s/landing.ridjal.com/planding.ridjal.com/g" landing.yml')
                }
           }
        stage('deploy') {
            steps {
                sh('kubectl apply -f landing.yml')
                }
           }
        stage('remove image docker') {
            steps {
                sh "docker rmi $DOCKER_REGISTRY/$DOCKER_IMAGE_NAME:$BUILD_NUMBER"
                }
           }
         stage('show ingress') {
            steps {
                sh('kubectl get ingress')
                }
           }        
      }
=======
        stage('RUNING') {
            steps {
                sh('sed -i "s/tag/$BUILD_NUMBER/g" index.html')
                sh "docker build --build-arg APP_NAME=$DOCKER_IMAGE_NAME -t $DOCKER_REGISTRY/$DOCKER_IMAGE_NAME:$BUILD_NUMBER ."
                sh "docker push $DOCKER_REGISTRY/$DOCKER_IMAGE_NAME:$BUILD_NUMBER"
                sh('sed -i "s/tag/$BUILD_NUMBER/g" landing.yml')
                sh('sed -i "s/landing.ridjal.com/slanding.ridjal.com/g" landing.yml')
                sh('sed -i "s/default/staging/g" landing.yml')
                sh('kubectl apply -f landing.yml')
                sh "docker rmi $DOCKER_REGISTRY/$DOCKER_IMAGE_NAME:$BUILD_NUMBER"
                sh('kubectl get ingress')
            }
        }        
    }
>>>>>>> master
}
