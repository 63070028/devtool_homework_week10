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
                    sh "docker build -t chanapon/vote_cat_dog:1.0 ."
                    sh "docker push chanapon/vote_cat_dog:1.0"
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
