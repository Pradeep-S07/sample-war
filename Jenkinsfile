node{
   stage('SCM Checkout'){
     git 'https://github.com/javahometech/my-app'
   }
   stage('Checkout Source Code') {
      git branch: "dev", url: "$https://github.com/Pradeep-S07/sample-war.git"
   }
   stage('Compile-Package'){
      // Get maven home path
      def mvnHome = /usr/share/maven tool name: 'maven-3', type: 'maven' 
      sh "${mvnHome}/bin/mvn validate"
      sh "${mvnHome}/bin/mvn compile"
      sh "${mvnHome}/bin/mvn package"
   }
   stage('Deploy to Tomcat') {
      def warFile = findFiles(glob: '**/target/*.war')[0]
      sh "cp ${warFile.path} ${DEPLOY_PATH}"   
   }
   stage('Email Notification'){
      mail bcc: '', body: '''Hi Welcome to jenkins email alerts
      Thanks
      Hari''', cc: '', from: '', replyTo: '', subject: 'Jenkins Job', to: 'hari.kammana@gmail.com'
   }
   stage('Slack Notification'){
       slackSend baseUrl: 'https://hooks.slack.com/services/',
       channel: '#jenkins-pipeline-demo',
       color: 'good', 
       message: 'Welcome to Jenkins, Slack!', 
       teamDomain: 'javahomecloud',
       tokenCredentialId: 'slack-demo'
   }
}
