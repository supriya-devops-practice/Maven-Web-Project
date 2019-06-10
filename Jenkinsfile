#!groovy

node ('master'){
    
   

def mvnHOME = tool name : "Maven" , type : "maven"
    
   

 stage ('checkout code')
{
       
 git credentialsId: '9b9aa26e-db8d-4ede-b0f4-17e4439d2c32', url: 'https://github.com/supriya-devops-practice/Maven-Web-Project.git'
   
 }
   

 stage ('build')
{
        
        
sh "${mvnHOME}/bin/mvn clean package"
   
     }
          
         
 stage ('sonar report')
{
            
 sh "${mvnHOME}/bin/mvn sonar:sonar"
        
  }
          
      
    
stage ('upload artifact')
{
             
 sh "${mvnHOME}/bin/mvn deploy"
    
      }
          
          
stage ('deploy artifact on tomcat')
{
              
             
 sshagent(['Tomcat_credentials']) 
 {
             
sh "scp -o StrictHostKeyChecking=no target/*.war ec2-user@13.235.82.190:/opt/apache-tomcat-9.0.20/webapps/"

 }
          

}
       

}
    
    
