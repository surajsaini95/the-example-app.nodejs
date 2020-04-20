pipeline {
    agent any
    stages {
        stage('Parallel Stage'){
            parallel {
                stage ('Install Dependencies in aws') {
                    agent {
                        label "ubuntu_aws"
                    }
                    steps {
                        sh '''
                            curl -sL https://deb.nodesource.com/setup_10.x | sudo -E bash -
                            sudo apt install  nodejs -y
                        '''
                    }
                }
                stage ('Install Dependencies in gcp') {
                    agent {
                        label "ubuntu-gcp"
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
