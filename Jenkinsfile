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
                bat "mvn -f TestWebApp/pom.xml clean package"
            }
        }
        stage("Archive"){
            steps{
                archiveArtifacts artifacts: 'TestWebApp/target/*.war', followSymlinks: false
            }
        }
        stage("Deploy"){
            steps{
                bat "del C:\\Program Files\\Apache Software Foundation\\Tomcat 9.0\\webapps\\*.war"
                bat "copy C:\\Windows\\System32\\config\\systemprofile\\AppData\\Local\\Jenkins\\.jenkins\\workspace\\Pipeline_POC\\TestWebApp\\target\\*.war C:\\Program Files\\Apache Software Foundation\\Tomcat 9.0\\webapps\\"
            }
        }
    }
}
