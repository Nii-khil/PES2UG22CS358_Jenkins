pipeline {
    agent any
    stages {
        stage('Clone repository') {
            steps {
                checkout([$class: 'GitSCM',
                branches: [[name: '*/main']],
                userRemoteConfigs: [[url: 'https://github.com/Nii-khil/PES2UG22CS358_Jenkins.git']]])
            }
        }
        stage('Build') {
            steps {
                build 'PES2UG22CS358-1'
                // introducing an error by using a non-existent file
                sh 'g++ doesntExist.cpp -o output'
            }
        }
        stage('Test') {
            steps {
                sh './output'
            }
        }
        stage('Deploy') {
            steps {
                echo 'deploy'
            }
        }
    }
    post {
        failure {
            error 'Pipeline failed'
        }
    }
}
