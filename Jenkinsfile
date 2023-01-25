pipeline {
    agent any 
    stages{
        stage('Code'){
            steps{
            git url: 'https://github.com/Ad1tya-Pandey/node-todo-cicd.git', branch: 'master'
            }
        }
        stage('build'){
            steps{
                sh 'docker build . -t ad1tyapandey/node-todo-test:latest'
                 
                
            
            }
        }
        stage('push '){
            steps{
                 withCredentials([usernamePassword(credentialsId: 'Dockerhub', passwordVariable: 'DOCKER_PASSWORD', usernameVariable: 'DOCKER_USERNAME')]) {
                    // Deploy the code to Dockerhub
                    sh "docker login -u $DOCKER_USERNAME -p $DOCKER_PASSWORD"
                    sh "docker push  ad1tyapandey/node-todo-test:latest"
                }
                

            }
        }
        stage('Test'){
            steps{
                echo "testing the build"
            }
        }
        stage('Deploy'){
            steps{
                sh "docker-compose down && docker-compose up -d"
            }
        }
        
    }
    
}
