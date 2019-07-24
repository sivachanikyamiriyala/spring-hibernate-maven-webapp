pipeline 
{
    agent any
    {
        stages
        {
            stage('continuous download')
            {
                steps
                {
                    git credentialsId: 'githubcredentials', url: 'https://github.com/sivachanikyamiriyala/spring-hibernate-maven-webapp.git'
                }
            }
            stage('validate compile and test')
            {
                steps
                {
                    sh 'mvn validate compile test'
                }
            }
            stage('cobertura and javaodc')
            {
                steps
                {
                    sh 'mvn cobertura:cobertura -Dcobertura.report.format=xml javadoc:javadoc'
                }
            }
            stage('contin build')
            {
                steps
                {
                    sh 'mvn package'
                }
            }
            
            
        }
    }

}
