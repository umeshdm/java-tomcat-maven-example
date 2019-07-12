node{
      def mvnHome = tool name: 'maven 3.5.4', type: 'maven' 
      stage('Checkout'){
         git 'https://github.com/LovesCloud/java-tomcat-maven-example'
       
      }  
      stage('Build'){
         //// Get maven home path and build
        // def mvnHome =  tool name: 'maven 3.5.4', type: 'maven'   
         sh "${mvnHome}/bin/mvn clean package -Dmaven.test.skip=true"
      }
     stage ('Test-JUnit'){
         //def mvnHome =  tool name: 'maven 3.5.4', type: 'maven'    
         sh "'${mvnHome}/bin/mvn' test surefire-report:report"
      }  
    
      stage('Deploy') {     
           //sshagent(['9d1832eb-7d79-43ca-ab91-f2a1140c4a4a']) {
           sshagent(['Tomcat-jenkins']) {
               sh 'scp -o StrictHostKeyChecking=no target/tomcatdeploymnetdemo.war jenkins@35.193.54.220:/opt/tomcat/webapps'
               //sh 'scp -o StrictHostKeyChecking=no target/tomcatdeploymnetdemo.war ubuntu@34.68.163.39:/home/ubuntu'
          }
         
     }
      
 }
