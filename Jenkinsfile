pipeline {
    agent {
        node {
            label 'AGENT-1'
        }
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
        stage('Deploy') {
            steps {
                echo 'Deploying....'
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