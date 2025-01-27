pipeline {
 environment {
 registry = "pedromasa/webapp"
 registryCredential = 'dockerhub_id'
 dockerImage = ''
 }
 agent any
 stages {
 stage('Cloning') {
 steps {
 //git 'https://github.com/pmasa/CICD.git'
 }
 }
 stage('Building Docker Image') {
 steps{
 script {
 //dockerImage = docker.build registry + ":$BUILD_NUMBER"
 }
 }
 }
 stage('Push Image to Docker Hub ') {
 steps{
 script {
 //docker.withRegistry( '', registryCredential ) {
 //dockerImage.push()
 //dockerImage.push('latest')
 //
 }}
 }}

 }
}
