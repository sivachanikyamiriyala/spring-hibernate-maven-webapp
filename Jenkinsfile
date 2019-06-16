 pipeline
{
  agent any
  stages
  {
    stage('continous download')
    {
      steps
      {
        git 'https://github.com/sivachanikyamiriyala/spring-hibernate-maven-webapp.git'
      }
    }
    stage('continous validata and compile')
    {
      steps
      {
        sh 'mvn validate compile'
      }
    }
    stage('continuous test')
    {
      steps
      {
        sh 'mvn test'
      }
    }
    stage('continuous code coverage')
    {
      steps
      {
        sh 'mvn cobertura:cobertura -Dcobertura.report.format=xml'
      }
    }
    stage('continous documentation preparation')
    {
      steps
      {
        sh 'mvn javadoc:javadoc'
      }
    }
    stage('static code analysis')
    {
      steps 
      {
        sh 'mvn compile sonar:sonar'
      }
    }

  }
}
