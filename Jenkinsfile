node('master')
{
 stage('continuous download')
 {
  git credentialsId: 'githubcredentialsoftheproject', url: 'https://github.com/sivachanikyamiriyala/spring-hibernate-maven-webapp.git'
 }
 stage('continuous validate and compile')
 {
  sh 'mvn validate compile'
 }
 stage('continuous unit testing')
 {
  sh 'mvn test'
 }
 stage('continuous cobertura code tesing')
  {
   sh 'mvn cobertura:cobertura -Dcobertura.report.format=xml'
  }
 stage('continuous preparation of java doc')
 {
  sh 'mvn javadoc:javadoc'
 }
 stage('continuous static code analysis')
 {
  sh 'mvn compile sonar:sonar'
 }
 stage('continuous build and release to nexus')
 {
  sh 'mvn package'
 }
stage('nexus uploader')
 {
  nexusArtifactUploader artifacts: [[artifactId: '**/*.war', classifier: '', file: '/var/lib/jenkins/workspace/scriptedpipeline/target/SpringHibernateExample-2.0.8.war', type: 'war']], credentialsId: 'nexuscredentials', groupId: 'repo', nexusUrl: '54.80.208.32:8081/nexus', nexusVersion: 'nexus2', protocol: 'http', repository: 'repo', version: '$BUILD_ID'
 }
stage('continuous deployment to testing servers')
{
 sh 'scp /var/lib/jenkins/workspace/scriptedpipeline/target/SpringHibernateExample-2.0.8.war centos@10.1.2.100:/home/centos/apache-tomcat-7.0.94/webapps/siva1.war'
}
 stage('continuous testing')
 {
  git 'https://github.com/sivachanikyamiriyala/FunctionalTesting.git'
 }
 stage('continuous delivery')
 {
  input message: 'waiting for the approval', submitter: 'ravi'
 sh 'scp /var/lib/jenkins/workspace/scriptedpipeline/target/SpringHibernateExample-2.0.8.war centos@10.1.1.100:/home/centos/apache-tomcat-7.0.94/webapps/siva2.war'
 }
}
