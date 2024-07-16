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
                    sh 'docker build -t habibul786/springPetclinic:latest'
                   }
           }
         stage('Imagepush') {
            steps {
                    sh 'docker push habibul786/springPetclinic:latest'
                   }
           }
       }
   }
