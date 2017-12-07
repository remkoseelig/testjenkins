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
                milestone ordinal: 1000, label: 'deploy to test?'
                input message: 'Move on and deploy to Test?', ok: 'Yes please!'
                milestone ordinal: 1001, label: 'deploy to test'
                echo "Deploying to Test..."
            }
        }
        stage('Deploy AQ') {
            steps {
                milestone ordinal: 2000, label: 'deploy to QA?'
                input message: 'Move on and deploy to QA?', ok: 'Yes please!', submitter: 'qa'
                milestone ordinal: 2001, label: 'deploy to QA'
                echo "Deploying to QA..."
            }
        }
    }
}
