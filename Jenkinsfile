node {
    def app

     stage('Clone repository') {
         checkout scm
     }
     stage('Build image') {
         app = docker.build("wnstn385/auth")
     }
     stage('Push image') {
            docker.withRegistry('https://registry.hub.docker.com', 'docker-hub') {
                app.push("${env.BUILD_NUMBER}")
                app.push("latest")
                sleep 3
                sh "docker rmi registry.hub.docker.com/wnstn385/auth:${env.BUILD_NUMBER}"
            }
         
     }

    //  stage('Trigger Manifest') {
    //      build job: "updatemanifest", parameters: [string(name: 'DOCKERTAG', value: env.BUILD_NUMBER)]
    //      }        

 }