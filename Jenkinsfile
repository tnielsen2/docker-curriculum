node {

def dockerapp
def ecrapp
    /* Let's set the environment variable for the development environment */
    environment {
        ENV = "${env.BRANCH_NAME}"
    }
    stage('Clone repository') {
        /* Let's make sure we have the repository cloned to our workspace */

        checkout scm
    }
    stage('Build Dockerhub image') {
            /* This builds the actual image in the folder above root */

            dockerapp = docker.build("yamtechnology/flask:${env.ENV}", "-f ./flask-app/Dockerfile ./flask-app/. ")
    }
    stage('Push image to Dockerhub') {
        /* Push to Dockerhub */
        docker.withRegistry('https://registry.hub.docker.com', '627b1088-462c-4adf-9e9a-0dee54655bd5') {
            dockerapp.push("${env.BRANCH_NAME}")
        }
    }
    stage('Build ECR image') {
            /* This builds the actual image in the folder above root */

            ecrapp = docker.build("flask:${env.ENV}", "-f ./flask-app/Dockerfile ./flask-app/. ")
    }
    stage('Push image to ECR') {
        /* Push to ECR */
        docker.withRegistry('https://264622616033.dkr.ecr.us-west-2.amazonaws.com/flask', 'ecr:us-west-2:sa-pxg-jenkins') {
            ecrapp.push("${env.BRANCH_NAME}")
        }
    }



}
