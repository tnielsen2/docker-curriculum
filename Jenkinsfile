pipeline {
    agent any
    environment {
    ENV = "develop"
}
stages {
    stage('Build image') {
    checkout scm

    docker.withRegistry('https://registry.hub.docker.com', '627b1088-462c-4adf-9e9a-0dee54655bd5') {

        def customImage = docker.build("yamtechnology/flask:${env.GIT_BRANCH}")

        /* Push the container to the custom Registry */
        customImage.push()

      }
   }
}
}
