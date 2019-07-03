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
    stage('nexus release ')
    {
     nexusArtifactUploader artifacts: [[artifactId: 'SpringHibernateExample-2.0.2.war', classifier: '', file: '/var/lib/jenkins/workspace/scriptedpipeline/target/SpringHibernateExample-2.0.2.war', type: 'war']], credentialsId: 'nexuscredentials', groupId: 'repo', nexusUrl: '54.235.232.205:8081/nexus', nexusVersion: 'nexus2', protocol: 'http', repository: 'repo', version: '$BUILD_ID'
    }
}
