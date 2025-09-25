pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo "Running hello.py..."
                sh 'python3 hello.py'
            }
        }

        stage('Testing') {
            steps {
                echo "Installing and running pytest..."
                sh 'python3 -m pip install --user pytest'
                sh 'python3 -m pytest > result.txt'
            }
        }

        stage('Archive Artifact') {
            steps {
                echo "Archiving test result..."
                archiveArtifacts artifacts: 'result.txt', fingerprint: true
            }
        }
    }
}
