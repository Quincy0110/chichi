pipeline {
    agent {label 'sama5d2'}
    stages {
        stage('Build') {
            steps {
                echo 'sh "./build01.sh"'
                
            }
        }
        
        stage('deploy') {
            steps([$class: 'BapSshPromotionPublisherPlugin']) {
                script {
                    List SERVERS_LIST = ["sama5d2"]
                    for(cr_server in SERVERS_LIST){
                        sshPublisher(
                            publishers: [
                                sshPublisherDesc(
                                    configName: cr_server, 
                                    verbose: true,
                                    transfers: [
                                        sshTransfer(
                                            execCommand: '', 
                                            sourceFiles: 'test.txt',
                                            cleanRemote: false, 
                                            excludes: '',
                                            execTimeout: 120000, 
                                            flatten: false, 
                                            makeEmptyDirs: false, 
                                            noDefaultExcludes: false, 
                                            patternSeparator: '[, ]+', 
                                            remoteDirectory: '', 
                                            remoteDirectorySDF: false, 
                                            removePrefix: ''
                                        ),
                                        
                                    ],
                                    usePromotionTimestamp: false, 
                                    useWorkspaceInPromotion: false, 
                                   
                                )
                            ]
                        )
                    }
                }
            }
        }
        
        
    }
    post {
        success { junit 'test_reports/*.xml' }
        unstable { echo 'HMMMMM' }
        failure { echo 'NOOOOOO' }
    }
}
