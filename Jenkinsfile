node('master') 
{
    stage('ContinuousDownload_loans') 
    {
         git 'https://github.com/thotasainath132/maven.git'
    }
     stage('ContinuousBuild_loans') 
    {
        sh label: '', script: 'mvn package'
    }
    stage('ContinuousDeployment')
    {
        sh label: '', script: 'scp /home/ubuntu/.jenkins/workspace/scriptedpipeline/webapp/target/webapp.war ubuntu@172.31.40.157:/var/lib/tomcat8/webapps/qaapp.war'
    }
    stage('ContinuousTesting')
    {
        git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
        sh label: '', script: 'java -jar /home/ubuntu/.jenkins/workspace/scriptedpipeline/testing.jar'
    }
    
  }
