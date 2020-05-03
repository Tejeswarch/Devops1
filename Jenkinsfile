pipeline {
  agent any 
  tools {
    maven 'M2_HOME'
  }
  stages {
    stage ('Initialize-Maven') {
      steps {
        sh '''
                    echo "PATH = ${PATH}"
                    echo "M2_HOME = ${M2_HOME}"
            ''' 
      }
    }  
    stage ('Build-War-File') {
      steps {
      sh 'mvn clean package'
       }
    }
      stage ('Deploy-To-Tomcat') {
            steps {
           sshagent(['tomcat']) {
                sh 'scp -o StrictHostKeyChecking=no target/*.war ec2-user@18.220.210.186:/opt/apache-tomcat-8.5.54/webapps/webapp.war'
              }      
           }       
   } 
    
  }
