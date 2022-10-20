pipeline{
    agent any

     stages {

         stage ("Build Docker Image") {
            steps {
                script {
                    dockerapp = docker.build("edusantos01/kube-news:${env.BUILD_ID}", '-f ./src/Dockerfile ./src')
                }
            }

         }
         stage ("Push Docker Image")  {
            steps {
                script {
                    docker.withRegistry('https://registry.hub.docker.com', 'devops')
                        dockerapp.push('latest')
                        dockerapp.push("${env.BUILD_ID}")
                }
            }
         }


     }

}