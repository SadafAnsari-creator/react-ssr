pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scmGit(branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/SadafAnsari-creator/react-ssr']])
            }
        }

        stage('Build') {
            steps {
                sh 'npm install'
                sh 'npm run build'
            }
        }

        stage('Deploy to AWS') {
            steps {
                deploy adapters: [tomcat9(path: '', url: 'http://3.109.152.61:8080')], contextPath: '/app', war: '**/*.war'
            }
        }
    }
}
