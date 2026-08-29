pipeline {
    // agent any
    agent {
        node {
            label 'ROBOSHOP'
        }
    }
    environment {
        myBranch = "Jenkins"
        EMAIL = "ramcharan@gmail.com"
    }
    stages {
        stage('Build') {
            steps {
                script {
                    sh """
                        echo "Building"
                        echo "The current branch is ${myBranch}"
                        echo "The current email is ${EMAIL}"
                    """
                }
            }
        }
        stage('Test') {
            steps {
                script {
                    sh """
                        echo "Testing"
                    """
                }
            }
        }
        stage('Deploy') {
            steps {
                script {
                    sh """
                        echo "Deploying"
                    """
                }
            }
        }
    }

    post {
        always {
            echo 'I always say hello again!!!'
        }
        success {
            echo 'Hurrayyyy pipeline succeeded!!!!!!'
        }
        failure {
            echo 'Ohh noooooo pipeline failed!!!!!!'
        }
        unstable {
            echo 'Something is fishy here!!!!'
        }
        aborted {
            echo 'My master has aborted me :(';
        }
    }
}