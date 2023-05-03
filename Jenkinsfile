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

                        deploy contextPath: 'http://localhost:8081/', war: '**/*.war'            }
        }
    }
}
