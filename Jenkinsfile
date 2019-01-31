node 
{
stage('Project Name')
{
echo 'This is Opstree CI CD'
}

stage('Checkout Code')
{
git 'https://github.com/harishkolanu235/CompleteCICDPipeline'
}

stage('Build Code')
{

sh 'mvn clean install -Dmaven.test.failure.ignore=true'
}

stage ('JUnit report')
{
    archive "target/**/*"
    junit 'target/surefire-reports/*.xml' 
}


 
 
 stage('Slage notification')
 {
 
 slackSend baseUrl: 'https://hooks.slack.com/services/', channel: '#jenkinspipelinedemo', color: 'good', message: 'Welcome to jenkins, slack !', teamDomain: 'Ashutosh DevOps', tokenCredentialId: 'slackdemo'

 
 }
 
 stage('Deploy to Tomcat')
{  
	  sshagent(['apachetomcat']) 
    {
    sh 'scp -o StrictHostKeyChecking=no target/*.war ubuntu@13.233.162.162:/var/lib/tomcat8/webapps/'
    }
	  
   }
  
	
 stage('Email notification')
{
mail bcc: '', body: '''HI welcome 
jenkins email alert
thanks
Ashutosh''', cc: 'ashutoshkumar101094@gmail.com', from: '', replyTo: '', subject: 'Jenkins Job', to: 'ashutoshkumar101094@gmail.com,ashutosh.kumar@pb.com'


}
	

}
