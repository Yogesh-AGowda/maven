pipeline{
    agent {
        label 'linuxagent'
    }
    tools{
        maven 'MAVEN_HOME'
    }
    stages{
        stage ('Build'){
            steps{
                sh 'mvn clean package'
            }
            post{
                success{
                    echo "Archiving the Artifacts"
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
        stage ('Deploy to tomcat server') {
            steps{

                deploy adapters: [tomcat9(credentialsId: '7e302c80-c016-4bb8-8456-2121799c568b', path: '', url: 'http://localhost:8081/')], contextPath: null, war: '**/*.war'
            }
        }
    }
}
