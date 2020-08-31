currentBuild.displayName="StudentSPring boot-#"+currentBuild.number


//This is the Declarative Pipeline Script
pipeline{
    agent any 
     stages{
//Build the Docker Image based on the Dockerfile
        stage('Build Docker Image'){
	  steps{
	     sh "sudo docker build -t maniengg/springboot1.2:${BUILD_ID}"   //when we run docker in this step, we're running it via a shell on the docker build-pod container
                        }
       }
 // Pushing the Docker Image to DockerHub   
     stage('Push Docker Image'){
	steps{
//Docker Hub Credentials
        withCredentials([string(credentialsId: 'DOKCER_HUB_PASSWORD', variable: 'DOKCER_HUB_PASSWORD')]) {
          sh "sudo docker login -u maniengg -p ${DOKCER_HUB_PASSWORD}"
          sh "sudo docker push maniengg/springboot1.2:${BUILD_ID}"
	              }
           }
       }    
     
    }
