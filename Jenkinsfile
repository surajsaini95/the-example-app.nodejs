pipeline {
    agent any
    stages {
        stage('Parallel Stage'){
            parallel {
                stage ('Install Dependencies in ubuntu Slave') {
                    agent {
                        label "ubuntu-slave"
                    }
                    steps {
                        sh '''
                            curl -sL https://deb.nodesource.com/setup_10.x | sudo -E bash -
                            sudo apt install  nodejs -y
                        '''
                    }
                }
                stage ('Install Dependencies in debian Slave') {
                    agent {
                        label "debian-slave"
                    }
                    steps {
                        sh '''
                            curl -sL https://deb.nodesource.com/setup_10.x | sudo -E bash -
                            sudo apt install  nodejs -y
                        '''
                    }
                }
            }
        }
        stage ('deployment') {
            steps {
            sh 'npm install && npm run start:dev'
            }
        }
    }
}
