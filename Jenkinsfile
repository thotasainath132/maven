node('master') 
{
    stage('ContinuousDownload_master') 
    {
         git 'https://github.com/thotasainath132/maven.git'
    }
     stage('ContinuousBuild_master') 
    {
        sh label: '', script: 'mvn package'
    }
    stage('ContinuousDeployment_master')
    {
        sh label: '', script: 'scp /home/ubuntu/.jenkins/workspace/scriptedpipeline/webapp/target/webapp.war ubuntu@172.31.40.157:/var/lib/tomcat8/webapps/qaapp.war'
    }
    stage('ContinuousTesting_master')
    {
        git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
        sh label: '', script: 'java -jar /home/ubuntu/.jenkins/workspace/scriptedpipeline/testing.jar'
    }
     stage('ContinuousDelivery_master')
    {
        sh label: '', script: 'scp /home/ubuntu/.jenkins/workspace/scriptedpipeline/webapp/target/webapp.war ubuntu@172.31.43.104:/var/lib/tomcat8/webapps/prodapp.war'
    }
    
 }
