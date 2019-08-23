pipeline {
    agent any
    environment {
    ENV = "develop"
}
    stages {
        stage('Build') {
            steps {
                sh('printenv | sort')
            }
        }
        stage('Test') {
            steps {
                echo $ENV
            }
        }
        stage('Deploy') {
            steps {
                echo 'Put deploy steps here'
            }
        }
    }
}
