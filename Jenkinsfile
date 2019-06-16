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
    stage('continous build')
    {
      steps
      {
        sh 'mvn package'
      }
    }
    stage('nexus release')
    {
      steps
      {
        nexusArtifactUploader artifacts: [[artifactId: 'SpringHibernateExample-2.0.2.war', classifier: '', file: '/var/lib/jenkins/workspace/declarativepipeline/target/SpringHibernateExample-2.0.2.war', type: 'war']], credentialsId: 'nexus--credentials', groupId: 'repo', nexusUrl: '3.82.249.140:8081/nexus', nexusVersion: 'nexus2', protocol: 'http', repository: 'repo', version: '$BUILD_ID'
      }
    }
    stage('deplot to qaserver')
    {
      steps
      {
        sh 'scp /var/lib/jenkins/workspace/declarativepipeline/target/SpringHibernateExample-2.0.2.war centos@10.1.1.171:/home/centos/apache-tomcat-7.0.94/webapps/z.war'
      }
    }
    

  }
}
