pipeline{
    agent any
    stages{
        stage("Clone"){
            steps{
                git branch: 'main', credentialsId: 'd343bf18-8846-46d6-b9f6-66a6620ffcb9', url: 'https://github.com/betkarakash/WebAppCICD_POC.git'
            }
        }
        stage("Build"){
            steps{
                bat "mvn -f TestWebApp/pom.xml clean install"
            }
        }
        stage("Archive"){
            steps{
                archiveArtifacts artifacts: 'TestWebApp/target/*.war', followSymlinks: false
            }
        }
    }
}
