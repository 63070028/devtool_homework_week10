pipeline {
    agent any

    environment {
		DOCKERHUB_CREDENTIALS=credentials('dockerhub')
	}
 
    stages {
        
        stage('Build Container') {
            steps {
                dir('devtool_homework_week10') {
                    echo "Current path is ${pwd()}"
                    sh "docker-compose down --rmi all --volumes || true"
                    echo "Create Container of docker-compose"
                    sh "docker-compose up -d"
                }
            }
        }

        stage('Login Dockerhub') {

			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}

        stage('Push To Dockerhub') {
            steps {
                dir('devtool_homework_week10') { 
                    echo "Current path is ${pwd()}"
                    echo "Push Image To Dockerhub"
                    sh "docker compose push"
                }
                }
            }

         stage('Delete  containers and images') {
            steps {
                dir('devtool_homework_week10') {
                    sh "docker stop \$(docker ps -a -q)"
                    sh "docker rm \$(docker ps -a -q)"
                    sh "docker rmi \$(docker images -q)"
                }
                }
            }
        

        stage('Send to Slave build in Production') {
            steps {
                build job: 'production_pipeline';
            }
        }

    
       

    }

    post {
		always {
			sh 'docker logout'
		}
	}
    

}


//test