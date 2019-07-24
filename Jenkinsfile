pipeline
{
agent any
stages
 {
  stage('continuous download')
  {
   steps
   {
    git credentialsId: 'githubcredentials', url: 'https://github.com/sivachanikyamiriyala/spring-hibernate-maven-webapp.git'
   }
  }
  stage('validateandcompile')
  {
   steps
   {
    sh 'mvn validate compile'
   }
  }
  stage('staticcodeanalysis')
  {
   steps
   {
    sh 'mvn sonar:sonar'
   }
  }
  stage('testing the code')
  {
   steps
   {
    sh 'mvn test'
   }
  }
  stage('cobertura')
  {
  steps
   {
    sh 'mvn cobertura:cobertura -Dcobertura.report.format=xml'
   }
  }
  stage('package')
  {
  steps
  {
  sh 'mvn package'
  }
  }
  stage('nexus artifact uploader')
  {
  steps
  {

  }
  }
 }
}
