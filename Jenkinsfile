pipeline {
    agent any
 
 stages {
      stage('checkout') {
           steps {
             
                git branch: 'main', url: 'https://github.com/mansi240992/PHP-project.git'
             
          }
        }
   stage('Docker Build and Tag') {
           steps {
              
                sh 'docker build -t my-php-image:latest .' 
                sh 'docker tag my-php-image mansi1992/my-php-image:latest'
                
               
          }
        }
     
  stage('Publish image to Docker Hub') {
          
            steps {
        withDockerRegistry([ credentialsId: "dockerhub", url: "" ]) {
          sh  'docker push mansi1992/my-php-image:latest'
        
        }
                  
          }
        }
     
      stage('Run Docker container on Jenkins Agent') {
             
            steps 
   {
                sh "docker run -d -p 8003:80 mansi1992/my-php-image:latest"
 
            }
        }

    }
 }
