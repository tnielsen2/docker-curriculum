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
                def flask = docker.build("yamtechnology/flask:${env.BRANCH_NAME}")
                customImage.push()
            }
         }
      }
   }
}
