#!groovy

pipeline {
  agent any
  stages {
    stage('Maven Install') {
      steps {
        sh './mvnw package'
      }
    }
    stage('Docker Build') {
      steps {
        sh 'docker build -t nibedita92/nibeditagit17:v7 .'
      }
    }
    stage('Docker Push') {
      steps {
        withCredentials([usernamePassword(credentialsId: 'dockerHub', passwordVariable: 'dockerHubPassword', usernameVariable: 'dockerHubUser')]) {
          sh "docker login -u ${env.dockerHubUser} -p ${env.dockerHubPassword}"
          sh 'docker push nibedita92/nibeditagit17:v7'
        }
      }
    }
  }
}
