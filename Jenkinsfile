node {    
      def app   
      stage("Build Maven"){
            withMaven{
                sh 'mvn package -DskipTests'
            }
      }  
      stage('Clone repository') {               
             
            checkout scm    
      }     
      stage('Build image') {         
       
            app = docker.build("brandonjones085/test")    
       }         
       stage('Push image') {
            docker.withRegistry('https://registry.hub.docker.com', 'git') {            
            app.push("${env.BUILD_NUMBER}")            
            app.push("latest")        
              }    
           }
        }
