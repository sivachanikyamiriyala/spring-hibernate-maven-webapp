node('master')
{
  stage('continuous download')
  {
    git 'https://github.com/sivachanikyamiriyala/spring-hibernate-maven-webapp.git'
  }
  stage('continuous validate and compile')
  {
    sh 'mvn validate compile'
  }
  stage('continuous testing of junit test cases')
  {
    sh 'mvn test'
  }
  stage('code coverage cobertura')
  {
    sh 'mvn cobertura:cobertura -Dcobertura.report.format=xml'
  }
  stage('documention')
  {
    sh 'mvn javadoc:javadoc'
  }
  stage('static code analysis')
  {
    sh 'mvn compile sonar:sonar'
  }
  stage('continuous build')
  {
    sh 'mvn package'
  }

}
