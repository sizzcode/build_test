pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                // Use the full path to your Python executable (from 'where python')
                // bat 'C:\\Users\\adith\\AppData\\Local\\Programs\\Python\\Python311\\python.exe hello_world.py'
                checkout scm
            }
        }
        stage('Build'){
            steps{
                echo 'Attempting to build...'
                sh 'python -m py_compile src/*.py'
            }
        }
    }
}
