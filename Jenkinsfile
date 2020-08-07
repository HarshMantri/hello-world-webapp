pipeline {
    agent any
    

    stages {
        stage('Fetching from Github') {
            steps {
                git 'https://github.com/HarshMantri/hello-world-webapp.git'
            }
        }
        
        stage('Build') {
            steps {
                
            }
        }
        
        stage('Deploy') {
            steps {
                script {
                    withDockerRegistry(
                        credentialsId: 'jenkins-creds-for-docker-hub',
                        toolName: 'docker') {
                        
                        def dockerImage = docker.build("harshmantri/hello-world-webapp:latest");
                        dockerImage.push();
                    }
                }
            }
        }
    }
}
