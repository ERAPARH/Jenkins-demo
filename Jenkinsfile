pipeline{
    agent any
stages{
    stage ('build'){
        steps{
            echo "run the python file"
           sh 'python3 hello.py'
        }
    }
stage('artifactbuild'){
    steps{
        echo 'Archiving the artifact output'
        archiveArtifacts artifacts: 'output.txt', fingerprint: true
    }
}

}
}
