node('master')
   {
    stage('continuous download')
    {
        git credentialsId: 'githubcredentials', url: 'https://github.com/sivachanikyamiriyala/spring-hibernate-maven-webapp.git'
    }
    stage('validate and compile')
    {
        sh 'mvn validate compile'
    }
    stage('continuous junit testing')
    {
        sh 'mvn test'
    }
    stage('continuous cobertura')
    {
        sh 'mvn cobertura:cobertura -Dcobertura.report.format=xml'
    }
    stage('continuous documentationpreparation')
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
