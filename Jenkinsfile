/* groovylint-disable-next-line CompileStatic */
pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git branch : 'main', url: 'https://github.com/agilewebwizards/devops-jenkins.git'
            }
        }
        stage('Install Dependencies') {
            steps {
                dir('jenkins-proj1') {
                    sh 'npm install'
                }
            }
        }
        stage('Build') {
            steps {
                dir('jenkins-proj1') {
                    sh 'npm run build'
                }
            }
        }
        stage('Test') {
            steps {
                dir('jenkins-proj1') {
                    sh 'npm test -- --watchAll=false --json --outputFile=test-result.json'
                }
            }
            post {
                always {
                    junit 'test-result.json'
                }
            }
        }
    }
}
