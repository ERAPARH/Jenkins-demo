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
        echo 'Creating Python virtual environment...'

        sh '''
            python3 -m venv venv
            ./venv/bin/python -m pip install --upgrade pip
            ./venv/bin/pip install pytest
            ./venv/bin/pytest
        '''
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
