
pipeline {
    agent any

    stages {

        stage('Checkout from Git') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/Srkgour/JENKINS-CONTINUOUS-INTEGRATION-COMPLETE-SETUP-FROM-AWS-EC2-TO-GITHUB-WEBHOOK.git'
            }
        }



        stage('Compile') {
            steps {
                    sh 'mvn clean compile'
                }
            }

        stage('Unit Tests') {
            steps {
                dir('JENKINS-CONTINUOUS-INTEGRATION-COMPLETE-SETUP-FROM-AWS-EC2-TO-GITHUB-WEBHOOK') {
                    sh 'mvn test'
                }
            }
        }

        stage('Package') {
            steps {
                    sh 'mvn clean package'
                }
            }

        stage('Archive Artifact') {
            steps {
                archiveArtifacts artifacts: 'JENKINS-CONTINUOUS-INTEGRATION-COMPLETE-SETUP-FROM-AWS-EC2-TO-GITHUB-WEBHOOK/target/*.jar',
                                 fingerprint: true
            }
        }
    }

    post {
        success {
            echo 'CI Pipeline completed successfully'
        }

        failure {
            echo 'CI Pipeline failed. Check Console Output.'
        }

        always {
            echo 'CI Pipeline execution completed'
        }
    }
}
