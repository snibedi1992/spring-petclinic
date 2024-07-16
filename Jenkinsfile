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
        sh 'docker build -t habibul786/springpetclinic:v5 .'
      }
    }
    stage('Docker Push') {
      steps {
        withCredentials([usernamePassword(credentialsId: 'dockerHub', passwordVariable: 'dockerHubPassword', usernameVariable: 'dockerHubUser')]) {
          sh "docker login -u ${env.dockerHubUser} -p ${env.dockerHubPassword}"
          sh 'docker push habibul786/springpetclinic:v5'
        }
      }
    }
  }
}
