pipeline {
    agent {label 'sama5d2'}
    stages {
        stage('Build') {
            steps {
                echo 'sh "./build01.sh"'
                
            }
        }
        
        stage('deploy') {
            steps {
                sh '''sshpass -p "root" ssh root@192.168.7.2 \'
                ls /mnt/data/etc

                \''''
            }
        }
        
        
    }
    post {
        success { junit 'test_reports/*.xml' }
        unstable { echo 'HMMMMM' }
        failure { echo 'NOOOOOO' }
    }
}
