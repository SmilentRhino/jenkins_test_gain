pipeline {
    agent any
    stages {
        stage('Clonde') {
            steps {
                sh 'pwd'
                sh 'ls'
                sh 'cat Jenkinsfile'
                git credentialsId: '33e35b80-2db3-4f65-ba2f-621628b51904', url: 'https://github.com/SmilentRhino/jenkins_test.git'
                echo 'Clone..'
            }
        }
        stage('Build') {
            steps {
                sh 'pwd'
                sh 'ls'
                sh 'cat Jenkinsfile'
            }
        }
        stage('Test') {
            environment {
                AN_ACCESS_KEY = credentials('bff24bf8-a05c-4bc7-8b36-b89fc0f80d8a')
            }
            steps {
                sh 'pwd'
                sh 'printenv'
                sh '/usr/bin/python test_password.py'
                sh 'ls'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
                dir('directoryToDelete') {
                    deleteDir()
                }
            }
        }
    }
    post {
        always {
            echo 'One way or another, I have finished'
            deleteDir() /* clean up our workspace */
        }
    }
}
