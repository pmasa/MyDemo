pipeline {
  environment {
    registry = "pedromasa/webapp"
    registryCredential = 'dockerhub_id'
    dockerImage = ''

  }
  agent any
  stages {
    stage('Cloning Git') {
      steps {
        git 'https://github.com/pmasa/CICD.git'
      }
    }
    stage('Building Docker image') {
      steps{
        script {
          dockerImage = docker.build registry + ":$BUILD_NUMBER"
          
        }
      }
    }
    stage('Push Image to Docker Hub') {
      steps{
        script {
          docker.withRegistry( '', registryCredential ) {
            dockerImage.push()
            dockerImage.push('latest')
          }
        }
      }
    }


stage ('Deploy') {
    steps{
        sh 'docker pull pedromasa/webapp:latest'
        sh 'docker stop webapp'
        sh 'docker rm webapp'
        sh 'docker rmi pedromasa/webapp:current || true'
        sh 'docker tag pedromasa/webapp:latest pedromasa/webapp:current'
        sh 'docker run -d --name webapp -p 8082:80 pedromasa/webapp:latest'
        
    }
}
      
    }

   
  }

