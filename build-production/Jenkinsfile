pipeline {
    agent any

 
    stages {
        stage('Initialize Stage') {
            steps {
            
                echo 'Initial : Delete  containers and images'
                 dir('devtool_homework_week10') { // change directory to Lab_docker_Jenkins
                    echo "Current path is ${pwd()}"
                    // sh "docker stop $(docker ps -a -q)"
                    // sh "docker rm $(docker ps -a -q)"
                    // sh "docker rmi $(docker images -q)"
                     sh "docker-compose down --rmi all --volumes || true"
                }
            }
        }


        stage('Build Container') {
            steps {
                dir('devtool_homework_week10') { // change directory to Lab_docker_Jenkins
                    echo "Current path is ${pwd()}"
                    echo "Create Container of docker-compose"
                    sh "docker-compose up -d"
                }
            }
        }

        stage('Push To Dockerhub') {
            steps {
                dir('devtool_homework_week10') { // change directory to Lab_docker_Jenkins
                    echo "Current path is ${pwd()}"
                    echo "Push Image To Dockerhub"
                    // withCredentials([usernamePassword(credentialsId: 'dckr_pat_8HklhCw27evFKot9bJF6GZcGChM', usernameVariable: 'chanapon', passwordVariable: 'Kong0')]) {
                    sh "docker compose push"
                }
                }
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
