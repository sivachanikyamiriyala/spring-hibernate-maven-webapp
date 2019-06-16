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
  stage('nexus release')
  {
    nexusArtifactUploader artifacts: [[artifactId: 'SpringHibernateExample-2.0.2.war', classifier: '', file: '/var/lib/jenkins/workspace/scriptedpipeline/target/SpringHibernateExample-2.0.2.war', type: 'war']], credentialsId: 'nexus--credentials', groupId: 'repo', nexusUrl: '3.82.249.140:8081/nexus', nexusVersion: 'nexus2', protocol: 'http', repository: 'repo', version: '$BUILD_ID'
  }
  stage('deployment to qaserver')
  {
    sh 'scp /var/lib/jenkins/workspace/scriptedpipeline/target/SpringHibernateExample-2.0.2.war centos@10.1.1.171:/home/centos/apache-tomcat-7.0.94/webapps/q1.war'
  }

}