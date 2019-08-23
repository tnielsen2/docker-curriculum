node {

def app
    /* Let's set the environment variable for the development environment */
    environment {
        ENV = "${env.GIT_BRANCH}"
    }
    stage('Clone repository') {
        /* Let's make sure we have the repository cloned to our workspace */

        checkout scm
    }
    stage('Build source image') {
            /* This builds the source image, without this, the subsequent step will fail */

            app = docker.build("python:3-onbuild")
    }
    stage('Build my image') {
            /* This builds the actual image; synonymous to
             * docker build on the command line */

            app = docker.build("yamtechnology/flask:${env.ENV}", "-f ./flask-app/Dockerfile ./. ")
    }

    stage('Push image') {
        /* Finally, we'll push the image with two tags:
         * First, the incremental build number from Jenkins
         * Second, the 'latest' tag.
         * Pushing multiple tags is cheap, as all the layers are reused. */
        docker.withRegistry('https://registry.hub.docker.com', '627b1088-462c-4adf-9e9a-0dee54655bd5') {
            app.push("${env.GIT_BRANCH}")
        }
    }



}
