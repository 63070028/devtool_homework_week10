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
                    //  sh "docker-compose down --rmi all --volumes || true"s
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
