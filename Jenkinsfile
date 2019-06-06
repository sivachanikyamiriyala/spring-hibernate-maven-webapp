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
}
