env.DOCKER_REGISTRY = 'rizaleko'
env.DOCKER_IMAGE_NAME = 'landing'
pipeline {
    agent any
    stages {
        
        stage('Git Pull from Github') {
            git credentialsId: 'githubpassword', url: 'https://github.com/Rizal-I/LandingPage.git'
            sh('sed -i "s/tag/$BUILD_NUMBER/g" index.html')
        }
        stage('Build Docker Image') {
            sh "docker build --build-arg APP_NAME=$DOCKER_IMAGE_NAME -t $DOCKER_REGISTRY/$DOCKER_IMAGE_NAME:$BUILD_NUMBER ."   
        }
        stage('Push Docker Image to Dockerhub') {
            sh "docker push $DOCKER_REGISTRY/$DOCKER_IMAGE_NAME:$BUILD_NUMBER"
        }   
        stage('TAGING on github Repo') {
            sh('sed -i "s/tag/$BUILD_NUMBER/g" landing.yml')
        }   
        //stage('Delete-app On Kubernetes Cluster') {
         //sh('kubectl delete -f landing.yml')
        //}
        stage('DeployTo Kubernetes Cluster') {
            sh('kubectl apply -f landing.yml')
        }
        stage('Remove Docker Image') {
            sh "docker rmi $DOCKER_REGISTRY/$DOCKER_IMAGE_NAME:$BUILD_NUMBER"   
        }
        stage('Get ingress') {
            sh('kubectl get ingress')
     }
  }
}
