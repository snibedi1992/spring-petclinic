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
                    sh 'docker build -t habibul786/springpetclinic:newtag .'
                   }
           }
         stage('Imagepush') {
            steps {
                    sh 'docker push habibul786/springpetclinic:newtag'
                   }
           }
       }
   }
