pipeline{
    agent any
    environment {
        PATH = "/usr/bin/mvn:$PATH"
    }
    stages{
        stage("build code"){
            steps{
                sh "mvn install"
            }
        }
        stage("test code"){
            steps{
                sh "mvn test"
            }
        }
        stage("code analysis"){
            withSonarQubeEnv("SonarQube"){
                sh """${scannerHome}/bin/sonar-sonner
                -Dsonar.login=admin \
                -Dsonar.password=admin@123 \
                -Dsonar.projectKey=online \
                -Dsonar.projectName='online' \
                -Dsonar.host.url=http://192.168.29.181:9000 \
                -Dsonar.token=sqa_acad5d12e9ee0bbc3a9546a1606b322365fa2722 \
                -Dsonar.language=java \
                -Dsonar.sourceEncoding=UTF-8/"""
            }
        } 
    }
}