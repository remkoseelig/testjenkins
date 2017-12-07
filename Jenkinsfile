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
        stage('Deploy Test') {
            steps {
                input message: 'Move on and deploy to Test?', ok: 'Yes please!'
                milestone 1, label: 'deploy to test'
                echo "Deploying to Test..."
            }
        }
        stage('Deploy AQ') {
            steps {
                input message: 'Move on and deploy to QA?', ok: 'Yes please!', submitter: 'qa'
                milestone 2, label: 'deploy to QA'
                echo "Deploying to QA..."
            }
        }
    }
}
