pipeline {
    agent {
        node {
            label 'ROBOSHOP'
        }
    }
    environment {
        COURSE = "Jenkins"
    }
    options {
        disableConcurrentBuilds()
        timeout(time: 5, unit: 'MINUTES')

    }
    parameters {
        string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should i say hello to?')
        text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')
        booleanParam(name: 'TOOGLE', defaultValue: true, description: 'Toogle this value')
        choice(name: 'CHOICE',choices: ['One', 'Two', 'Three'], description: 'Pick something')
        password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')

    }
    stages {
        stage('Build'){
            steps {
                script{
                    sh """
                        echo "Building application"
                        echo "Course name: $COURSE"
                        sleep 10
                      """
                }
            }
        }
        stage('Test'){
            steps{
                script{
                    sh """
                        echo "Running test"
                        echo "Hello ${params.PERSON}"
                        echo "Biography: ${params.BIOGRAPHY}"
                        echo "Toogle Value: ${params.TOGGLE}"
                        echo "Choice selected: ${params.CHOICE}"

                        echo "Password: ${params.PASSWORD}"
                    """
                }
            }
        }
        stage('Deploy'){
            steps{
                script{
                    sh """
                        echo "Deploying application"
                    """
                }
            }
        }
    }
    post {
        always {
            echo 'Pipeline execution Completed'
        }
        success {
            echo 'Pipeline executed successfully'
        }
        failure {
            echo 'pipeline execution failed'
        }
    }

}