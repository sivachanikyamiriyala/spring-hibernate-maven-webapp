node('master')
{
  stage('continuous download,valiadate and ocmpile code')
  {
    git credentialsId: 'githubcredentials', url: 'https://github.com/sivachanikyamiriyala/spring-hibernate-maven-webapp.git'
  }
  stage('continuous validate and compile')
  {
    sh 'mvn valiadate compile'
  }
  stage('continuous teting the unit test caess')
  {
    sh 'mvn test'
  }
  stage('continuous cobertutura report generation')
  {
    sh 'mvn cobertura:cobertura -Dcobertura.report.format=xml'
  }
  stage('continuous preparation of documentattoj')
  {
    sh 'mvn javadoc:javadoc'
  }
  stage('continuous static code analysis')
  {
    sh 'mvn compile sonar:sonar'
  }
  stage('package and release to nexus')
  {
    sh 'mvn package'
  }
  staeg('nexus release')
  {
    nexusArtifactUploader artifacts: [[artifactId: '**/*.war', classifier: '', file: '/var/lib/jenkins/workspace/scriptedpipeline/target/*.war', type: 'war']], credentialsId: 'nexuscredentials', groupId: 'repo', nexusUrl: '34.238.118.17:8081/nexus', nexusVersion: 'nexus2', protocol: 'http', repository: 'repo', version: '$BUILD_ID'
  }
}