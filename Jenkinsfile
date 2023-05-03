pipeline{
    agent any
    tools{
        maven 'MAVEN_HOME'
    }
    stages{
        stage ('Build'){
            steps{
                bat 'mvn clean package'
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

deploy adapters: [tomcat9(credentialsId: '7e302c80-c016-4bb8-8456-2121799c568b', path: '', url: 'http://localhost:8081')], contextPath: 'C:\\Users\\yogesh.gowda.IMANAGE\\.jenkins\\workspace\\maven\\target\\', war: '**/*.war'        }
    }
}
