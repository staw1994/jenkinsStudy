pipeline {
    agent any

    tools { 
        maven 'Maven 3.9.5'
        jdk 'JDK 17'
    }

    environment { 
        MAVEN_OPTS = '-Xmx1024m'
        APP_NAME = 'demo'
        APP_VERSION = '0.0.1-SNAPSHOT'
    }

    options {
        buildDiscarder (logRorator(numToKeepStr: '10'))
        timestamps()
        timeout(time: 30, unit: 'MINUTES')
    }

    stages { 
        stage('Checkout') { 
            steps { 
                echo 'start build 123 456'
            }
        }
        stage('Build') {
            steps {
                echo 'Building application'
            }
            post { 
                success { 
                    echo 'Builded success!'
                }
                failure { 
                    echo 'Builded failed!'
                }
            }
        }
        stage('Test') {
            steps {
                echo 'Testing application'
            }
            post {
                always { 
                    echo 'Testing result'
                }
            }
        }
        stage('Code reviewing') {
            steps {
                echo 'sona scan result: '
            }
        }

        stage('Deploy') {
            steps {
                echo 'start application deploy'
            }
            # deploy/upload new jar 
            # check jar is exist
            # remote deploy (ssh -T ${remoteHost})
            # stop old application
            # confirm old cpplication is stopped
            # start new application
            # verify new application is running (output error if any)
            post {
                success {
                    echo 'Deploy success!'
                }
                failure {
                    echo 'Deploy failured'
                }
            }
        }
    }
    post {
        always {
            echo 'Cleaning up workspace'
            cleanWs()
        }
        success {
            echo 'Pipeline completed successfully!'
        }
        failure{
            echo 'Pipeline failed!'
        }
    }
}