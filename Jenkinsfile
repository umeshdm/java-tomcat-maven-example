node{
      stage('Checkout'){
         git 'https://github.com/LovesCloud/java-tomcat-maven-example'
      }  
      stage('Build'){
         //// Get maven home path and build
         def mvnHome =  tool name: 'Maven 3.5.4', type: 'maven'   
         sh "${mvnHome}/bin/mvn package"
      }
      stage ('Test'){
         def mvnHome =  tool name: 'Maven 3.5.4', type: 'maven'    
         sh "${mvnHome}/bin/mvn test; sleep 3"
      }  
      stage('Deploy') {     
           sshagent(['9d1832eb-7d79-43ca-ab91-f2a1140c4a4a']) {            
                sh 'scp -o StrictHostKeyChecking=no target/tomcatdeploymnetdemo.war ubuntu@34.68.163.39:/opt/tomcat/webapps'
              //    sh 'scp -o StrictHostKeyChecking=no target/tomcatdeploymnetdemo.war ubuntu@34.68.163.39:/home/ubuntu'
          }
         
     }
      
 }
