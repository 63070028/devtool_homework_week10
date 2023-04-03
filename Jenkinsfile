pipeline {
    agent any

    environment {
		DOCKERHUB_CREDENTIALS=credentials('dockerhub')
	}
 
    stages {
        
        stage('Build Container') {
            steps {
                dir('devtool_homework_week10') { // change directory to Lab_docker_Jenkins
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
                dir('devtool_homework_week10') { // change directory to Lab_docker_Jenkins
                    echo "Current path is ${pwd()}"
                    echo "Push Image To Dockerhub"
                    sh "docker compose push"
                }
                }
            }
        

        stage('Build Production') {
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







// pipeline {
//     agent any

 
//     stages {
//         stage('Initialize Stage') {
//             steps {
            
//                 echo 'Initial : Delete  containers and images'
//                  dir('Lab_jenkins_dockercompose') { // change directory to Lab_docker_Jenkins
//                     echo "Current path is ${pwd()}"
//                     sh "docker-compose down --rmi all --volumes || true"
//                 }
//             }
//         }


//         stage('Build Stage') {
//             steps {
//                 dir('Lab_jenkins_dockercompose') { // change directory to Lab_docker_Jenkins
//                     echo "Current path is ${pwd()}"
//                     sh "docker-compose up -d"
//                 }
//             }
//         }

    
       

//     }
// }
