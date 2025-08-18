pipeline{
    agent any
    stages{
        stage('Checkout'){
            steps{
                git branch : 'main', url: "https://github.com/agilewebwizards/devops-jenkins.git"
            }
        }
        stage('Install Dependencies'){
            steps{
                sh 'npm install'
            }
        }
        stage('Build'){
            steps{
                sh 'npm run build'
            }
        }
        stage('Test'){
            steps{
                sh 'npm test -- --watchAll=false --json --outputFile=test-result.json'
            }
            post{
                always{
                    junit 'test-result.json'
                }
            }
        }
    }
}