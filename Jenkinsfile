node('master')
{
 stage('validate and compile')
 { 
  git credentialsId: 'githubcredentials', url: 'https://github.com/sivachanikyamiriyala/spring-hibernate-maven-webapp.git'
 }
 stage('testingjunit')
 {
  sh 'mvn validate compile'
 }
 stage('staticcode')
 {
  sh 'mvn sonar:sonar'
 }
 stage('test')
 { 
  sh 'mvn test'
 }
 stage('cobertura')
 {
  sh 'mvn cobertura:cobertura -Dcobertura.report.format=xml'
 }
 stage('package')
 {
  sh 'mvn sonar:sonar package'
 }
  stage('deploymet to nexus')
  {
   nexusArtifactUploader artifacts: [[artifactId: 'SpringHibernateExample-2.0.3.war', classifier: '', file: '/var/lib/jenkins/workspace/scriptedpipeline/target/SpringHibernateExample-2.0.3.war', type: 'war']], credentialsId: 'nexuscredentials', groupId: 'repo', nexusUrl: '54.172.130.5:8081/nexus', nexusVersion: 'nexus2', protocol: 'http', repository: 'repo', version: '$BUILD_ID'
  }
  stage('deployment to testing servers')
  {
    sh 'scp /var/lib/jenkins/workspace/scriptedpipeline/target/SpringHibernateExample-2.0.3.war centos@10.6.1.100:/home/centos/apache-tomcat-7.0.94/webapps/siva1.war'
  }
  stage('testing')
  {}
  stage('delivery')
  {
   sh 'scp /var/lib/jenkins/workspace/scriptedpipeline/target/SpringHibernateExample-2.0.3.war centos@10.6.1.149:/home/centos/apache-tomcat-7.0.94/webapps/siva1.war'
  }
}
