pipeline {
    agent any

    parameters {
        string(name: 'GIT_COMMIT', defaultValue: '', description: 'Git commit to build')
    }

    environment {
        GITHUB_REPO = "Sarayu-T/devops-assistant"
        FAILED_FILE = "main.py"  // Adjust if needed
        FLASK_TRIGGER_URL = "http://localhost:5000/webhook/jenkins"  // 🔁 Replace this
    }

    stages {
        stage('Clone Repository') {
            steps {
                script {
                    def repoUrl = "https://github.com/sizzcode/build_test.git"
                    def commit = params.GIT_COMMIT?.trim()
                    
                    if (commit) {
                        echo "📌 Cloning specific commit: ${commit}"
                        checkout([$class: 'GitSCM',
                            branches: [[name: commit]],
                            userRemoteConfigs: [[url: repoUrl]]
                        ])
                    } else {
                        echo "🔄 No commit specified, checking out 'main'"
                        git url: repoUrl, branch: 'main'
                    }
                }
            }
        }

        stage('Run Tests') {
            steps {
                script {
                    echo "🔍 Attempting to run tests..."

                    def result = bat(
                        script: "C:\\Users\\Pranathi\\AppData\\Local\\Microsoft\\WindowsApps\\python.exe hello_world.py",
                        returnStatus: true
                    )

                    echo "🔁 Exit code: ${result}"

                    if (result != 0) {
                        echo "❌ Test failed!"
                        error("Tests failed. Exiting pipeline.")
                    } else {
                        echo "✅ Test passed!"
                    }
                }
            }
        }
    }
}
