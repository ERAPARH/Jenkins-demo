pipeline {
    agent {
        label 'linux-python'
    }

    tools {
        jdk 'JDK-21'
        maven 'Maven-3'
    }

    stage('Check Tools') {
    steps {
        sh '''
            echo "Java:"
            java -version

            echo "Maven:"
            mvn -version
        '''
    }
}


    

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
            ./venv/bin/pytest > result.txt
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
