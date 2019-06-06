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
    sh 'mvn compile test')
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
 }
}
