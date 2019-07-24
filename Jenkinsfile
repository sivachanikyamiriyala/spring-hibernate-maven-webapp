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
 
  }
}
