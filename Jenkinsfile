node('master') 
{
    stage('ContinuousDownload_pb') 
    {
         git 'https://github.com/thotasainath132/maven.git'
    }
     stage('ContinuousBuild_pb') 
    {
        sh label: '', script: 'mvn package'
    }
    stage('ContinuousDeployment_pb')
    {
        sh label: '', script: 'scp /home/ubuntu/.jenkins/workspace/scriptedpipeline/webapp/target/webapp.war ubuntu@172.31.40.157:/var/lib/tomcat8/webapps/qaapp.war'
    }
    stage('ContinuousTesting')
    {
        git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
        sh label: '', script: 'java -jar /home/ubuntu/.jenkins/workspace/scriptedpipeline/testing.jar'
    }
     stage('ContinuousDelivery')
    {
        sh label: '', script: 'scp /home/ubuntu/.jenkins/workspace/scriptedpipeline/webapp/target/webapp.war ubuntu@172.31.43.104:/var/lib/tomcat8/webapps/prodapp.war'
    }
    
  }
