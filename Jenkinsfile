pipeline {
    agent any
    triggers {
        pollSCM('* * * * *')
    }
    stages {
        stage('vcs') {
            steps {
                git branch: 'main', url: 'https://github.com/iamsam2772/saleor-dashboard.git'
            }
        }
        stage('docker image build') {
            steps {
                sh 'docker image build -t iamsam2772/saleor-dashboar:DEV .'
            }
        }
        stage('image tagging') {
            steps {
                sh 'docker image tag iamsam2772/saleor-dashboar:DEV'
            }
        }
        stage('push image to registry') {
            steps {
                sh 'docker image push iamsam2772/saleor-dashboar:DEV'
            }
        }
    }
}
