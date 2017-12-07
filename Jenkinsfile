#!/usr/bin/env groovy

pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building...'
                sh 'ls -al'
                echo 'System info...'
                sh 'df -H'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing...'
            }
        }
        stage('Deploy', concurrency: 1) {
            steps {
                input message: 'Move on and deploy?', ok: 'Yes please!', submitter: 'qa'
                echo 'Deploying....'
            }
        }
    }
}
