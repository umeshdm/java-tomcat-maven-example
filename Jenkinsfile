node{
      stage('Checkout'){
         git 'https://github.com/LovesCloud/java-tomcat-maven-example'
      }  
      stage('Build'){
         //// Get maven home path and build
         def mvnHome =  tool name: 'maven 3.5.4', type: 'maven'   
         sh "${mvnHome}/bin/mvn package -Dmaven.test.skip=true"
      }
      /*stage ('Test'){
         def mvnHome =  tool name: 'maven 3.5.4', type: 'maven'    
         sh "${mvnHome}/bin/mvn test; sleep 3"
      }  
      */
      stage('Deploy') {     
           //sshagent(['9d1832eb-7d79-43ca-ab91-f2a1140c4a4a']) {
           sshagent(['tomcatsshagent']) {
               sh 'scp -o StrictHostKeyChecking=no target/tomcatdeploymnetdemo.war root@34.67.96.127:/opt/tomcat/webapps'
               //sh 'scp -o StrictHostKeyChecking=no target/tomcatdeploymnetdemo.war ubuntu@34.68.163.39:/home/ubuntu'
          }
         
     }
      
 }
