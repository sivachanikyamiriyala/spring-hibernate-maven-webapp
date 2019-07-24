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
  sh 'mvn sonar:sonar \-Dsonar.host.url=http://54.172.130.5:9000 \-Dsonar.login=2aa90c4891b2aefa17abd2c11cb4f642ee600832'
 }
 stage('test')
 { 
  sh 'mvn test'
 }
 stage('cobertura')
 {
  sh 'cobertura:cobertura -Dcobertura.report.format=xml'
 }
 stage('package')
 {
  sh 'mvn sonar:sonar package'
 }
  stage('deploymet to nexus')
  {
 
  }
}
