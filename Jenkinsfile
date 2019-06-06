pipeline
{
 agent any
 stages
 {
  stage('continuous download')
  {
   steps
   {
     git credentialsId: 'githubcredentialsoftheproject', url: 'https://github.com/sivachanikyamiriyala/spring-hibernate-maven-webapp.git'
   }
  }
  stage('continuous validatae compile test')
  {
   steps
   {
    sh 'mvn validate compile'
   }
  }
  stage('testing unit testin')
  {
   steps
   {
     sh 'mvn test'
   }
  }
  stage('continuous test the junit test cases')
  {
   steps
   {
    sh 'mvn cobertura:cobertura -Dcobertura.report.format=xml'
   }
  }
  stage('documentation')
  {
   steps
   {
    sh 'mvn javadoc:javadoc'
   }
  }
  stage('continuous static code analysis')
  {
   steps
   {
    sh 'mvn compile sonar:sonar'
   }
  }
  stage('package')
  {
  steps
  { 
   sh 'mvn package'
  }
  }
  stage('nexus uploader')
  {
  steps
  {
   nexusArtifactUploader artifacts: [[artifactId: '**/*.war', classifier: '', file: '/var/lib/jenkins/workspace/multibranch_master/target/SpringHibernateExample-2.0.8.war', type: 'war']], credentialsId: 'nexuscredentials', groupId: 'repo2', nexusUrl: '54.80.208.32:8081/nexus', nexusVersion: 'nexus2', protocol: 'http', repository: 'repo2', version: '$BUILD_ID'
  }
  }
  stage('continuous deployment')
  {
  steps
  {
   sh 'scp /var/lib/jenkins/workspace/multibranch_master/target/SpringHibernateExample-2.0.8.war centos@10.1.2.100:/home/centos/apache-tomcat-7.0.94/webapps/ram1.war'
  }
  }
  stage('continuous test')
  {
  steps
  {
   git 'https://github.com/sivachanikyamiriyala/FunctionalTesting.git'
  }
  }
 }
 post
 {
 success
 {
   sh 'scp /var/lib/jenkins/workspace/multibranch_master/target/SpringHibernateExample-2.0.8.war centos@10.1.1.100:/home/centos/apache-tomcat-7.0.94/webapps/ram2.war'
 }
 failure
 {
 mail bcc: '', body: '', cc: 'lead@gmail.com', from: '', replyTo: '', subject: '', to: 'siva@gmail'
 }
 }
}
