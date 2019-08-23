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
            /* This builds the actual image; synonymous to
             * docker build on the command line */

            app = docker.build("yamtechnology/flask:${env.ENV}", "-f ./flask-app/Dockerfile ./flask-app/. ")
    }

    stage('Push image') {
        /* Finally, we'll push the image with two tags:
         * First, the incremental build number from Jenkins
         * Second, the 'latest' tag.
         * Pushing multiple tags is cheap, as all the layers are reused. */
        docker.withRegistry('https://registry.hub.docker.com', '627b1088-462c-4adf-9e9a-0dee54655bd5') {
            app.push("${env.BRANCH_NAME}")
        }
    }
    stage('Identify This Branch') {
        echo ${env.BRANCH_NAME}"
        }
    }


}
