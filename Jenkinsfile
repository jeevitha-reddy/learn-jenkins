pipeline {
    agent {
        node {
            label 'AGENT-1'
        }
    }
    // other system url also can use 
    environment {
        GREETING = 'hello'
    }
    //time setup
    //one job is running two builds at a time we use concurrnce
    options {
        timeout(time:1, unit: 'HOURS')
        disableConcurrentBuilds()
    } 
    // accesing this value we can connect pipeline
    // accept the parameter variables is required
    parameters {
        string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')

        text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')

        booleanParam(name: 'TOGGLE', defaultValue: true, description: 'Toggle this value')

        choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')

        password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')
    } 
    //build
    stages {
        stage('Build') {
            steps {
                echo 'Building..'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        // after aplying environment we can use shell script
        stage('Deploy') {
            steps {
                sh """
                    echo "Deploying...."
                    echo "$GREETING"
                    sleep 10
                """
            }
        }
        // after adding first commit we won't get nexr commit we will get
         stage('check params'){
            steps{
                sh """
                    echo "Hello ${params.PERSON}"

                    echo "Biography: ${params.BIOGRAPHY}"

                    echo "Toggle: ${params.TOGGLE}"

                    echo "Choice: ${params.CHOICE}"

                    echo "Password: ${params.PASSWORD}"
                """
            }
        }
    }
    
    // post buld
    post {
        always {
            echo 'Hai Hello'
        }
        failure {
            echo 'pipeline s failed'
        }
        success {
            echo 'pipeline success'
        }
    }
}