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
    options {
        disableConcurrentBuilds()
        // timeout(time: 5, unit: 'SECONDS')
    }
    parameters {
        string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
        text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')
        booleanParam(name: 'DEPLOY', defaultValue: false, description: 'Toggle this value')
        choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')
        password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')
    }
    stages {
        stage('Build') {
            steps {
                script {
                    sh """
                        echo "Building"
                        echo "The current branch is ${myBranch}"
                        echo "The current email is ${EMAIL}"
                        # sleep 10
                    """
                }
            }
        }
        stage('Test') {
            steps {
                script {
                    sh """
                        echo "Testing"
                        echo "Hello ${params.PERSON}"
                        echo "Biography: ${params.BIOGRAPHY}"
                        echo "Toggle: ${params.TOGGLE}"
                        echo "Choice: ${params.DEPLOY}" 
                        echo "Password: ${params.PASSWORD}"
                    """
                }
            }
        }
        stage('Deploy') {
            input {
                message "Should we continue?"
                ok "Yes, we should."
                submitter "alice,bob"
                parameters {
                    string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
                }
            }
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
        // aborted {
        //     echo 'My master has aborted me :(';
        // }
    }
}