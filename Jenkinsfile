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
                echo "Running tests with pytest..."
                sh 'pip install pytest'           // Make sure pytest is available
                sh 'pytest > result.txt'          // Run tests and save output
            }
        }

        stage('Archive Artifact') {
            steps {
                echo "Saving result.txt as artifact..."
                archiveArtifacts artifacts: 'result.txt', fingerprint: true
            }
        }
    }
}
