pipeline {
    agent {label 'sama5d2'}
    stages {
        stage('Example') {
            steps {
                echo 'Hello World'
            }
        }
    }
    post {
        success { echo 'HURRAAAAAY' }
        unstable { echo 'HMMMMM' }
        failure { echo 'NOOOOOO' }
    }
}
