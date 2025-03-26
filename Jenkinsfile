pipeline {
    agent any
    stages {
        stage('Test') {
            steps {
                script {
                    try {
                        bat 'python hello_world.py'  // Windows
                        // sh 'python3 hello_world.py'  // Linux
                    } catch (Exception e) {
                        error("Python script failed! Build aborted.")  // Force failure
                    }
                }
            }
        }
    }
}
