pipeline {
    agent any
    stages {
        stage('Checkout'){
            steps{
                checkout scm
            }
        }
        stage('Run python Script') {
            steps {
                // Use the full path to your Python executable (from 'where python')
                bat 'py hello_world.py'
            }
        }

    }
}
