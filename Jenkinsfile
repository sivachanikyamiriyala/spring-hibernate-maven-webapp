node('master')
{
  stage('continuous download,valiadate and ocmpile code')
  {
    git credentialsId: 'githubcredentials', url: 'https://github.com/sivachanikyamiriyala/spring-hibernate-maven-webapp.git'
  }
  stage('continuous validate and compile')
  {
    sh 'mvn validate compile'
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
    
  }
  stage('depployment to qaserver')
  {
    sh 'scp /var/lib/jenkins/workspace/scriptedpipeline/target/SpringHibernateExample-2.0.2.war centos@10.1.1.171:/home/centos/apache-tomcat-7.0.94/webapps/qq.war'
  }
  stage('deployrmt to prod')
  {
    sh 'scp /var/lib/jenkins/workspace/scriptedpipeline/target/SpringHibernateExample-2.0.2.war centos@10.1.1.162:/home/centos/apache-tomcat-7.0.94/webapps/pp.war'
  }
}