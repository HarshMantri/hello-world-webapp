pipeline {
    agent any
    

    stages {
        stage('Fetching from Github') {
            steps {
                git 'https://github.com/HarshMantri/hello-world-webapp.git'
            }
        }
        
        stage('Requirements') {
            steps {
              	sh "pip install -r requirements.txt"  
            }
        }

	stage('Build') {
           steps {
		sh "python3 app.py"
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
