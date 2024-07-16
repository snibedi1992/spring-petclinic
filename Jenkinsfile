pipeline {
    agent any
     stages {
        stage('MavenPackage') {
            steps {
                sh './mvnw package'
             }
        }
         stage('DockerBuild') {
            steps {
                    sh 'docker build -t habibul786/springpetclinic:v2 .'
                   }
           }
         stage('Imagepush') {
            steps {
                    withCredentials([usernamePassword(credentialsId: '08a3db89-53b4-42d0-a5d7-57f071cf72da', passwordVariable: 'dockerHubPassword', usernameVariable: 'dockerHubUser')]) {
                    sh "docker login -u ${env.dockerHubUser} -p ${env.dockerHubPassword}"
                    sh 'docker push habibul786/springpetclinic:v2'
                   }
           }
       }
   }
}
