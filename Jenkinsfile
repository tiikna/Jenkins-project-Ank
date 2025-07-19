pipeline {
    agent any

    stages {
        stage('Clone Repo') {
            steps {
                git branch: 'main', url: 'https://github.com/tiikna/Jenkins-project-Ank.git'
            }
        }

        stage('Run Script') {
            steps {
                script {
                    def output = sh(script: "python3 hello.py", returnStdout: true).trim()
                    echo "Script output: ${output}"
                    currentBuild.description = output
                }
            }
        }
    }

    post {
        always {
            emailext(
                subject: "Build ${currentBuild.fullDisplayName}",
                body: "Build result: ${currentBuild.currentResult}\n\nOutput: ${currentBuild.description}",
                to: "themishraankit@gmail.com"
            )
        }
    }
}       
