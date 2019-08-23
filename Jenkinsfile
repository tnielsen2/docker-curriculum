pipeline {
    agent any
    environment {
    ENV = "develop"
}
stages {
    stage('Build image') {
        steps {
            echo 'Starting to build docker image'

            script {
                def flask = docker.build("yamgtechnology/flask:${env.BRANCH_NAME}")
                customImage.push()
            }
        }
    }
}
