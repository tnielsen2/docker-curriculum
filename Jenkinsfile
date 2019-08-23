node {

def app
    /* Let's set the environment variable for the development environment */
    environment {
        ENV = "${env.BRANCH_NAME}"
    }
    stage('Clone repository') {
        /* Let's make sure we have the repository cloned to our workspace */

        checkout scm
    }
    stage('Build my image') {
            /* This builds the actual image in the folder above root */

            app = docker.build("yamtechnology/flask:${env.ENV}", "-f ./flask-app/Dockerfile ./flask-app/. ")
    }
    stage('Push image to Dockerhub') {
        /* Push to Dockerhub */
        docker.withRegistry('https://registry.hub.docker.com', '627b1088-462c-4adf-9e9a-0dee54655bd5') {
            app.push("${env.BRANCH_NAME}")
        }
    }
    stage('Push image to ECR') {
        /* Push to ECR */
        docker.withRegistry('https://264622616033.dkr.ecr.us-west-2.amazonaws.com/flask', 'sa-pxg-jenkins') {
            app.push("${env.BRANCH_NAME}")
        }
    }



}
