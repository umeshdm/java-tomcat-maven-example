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
         sh "${mvnHome}/bin/mvn verify; sleep 3"
      }  
      stage('Deploy') {     
            def copyScript='sudo cp *.war /opt/tomcat/webapps'
          sshagent(['abeab169-3c7e-4291-98f3-7f190a3d4099']) {            
               sh 'scp -o StrictHostKeyChecking=no target/*.war ubuntu@52.90.151.183:/home/ubuntu'
               sh 'cp ubuntu@52.90.151.183:/home/ubuntu/*.war /opt/tomcat/webapps/' 
                //&& ${copyScript}'  
              // sh '${copyScript}'
              // sh 'ubuntu@52.90.151.183 cp  lovescloud.war /opt/tomcat/webapps'
           }
     }
      
 }
