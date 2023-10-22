pipeline{
    agent any
    environment {
        PATH = "/usr/bin/mvn:$PATH"
        def scannerHome = tool 'sonarQube'
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
        stage("Code Analysis"){
            steps{
                withSonarQubeEnv('sonarQube'){
                sh "${scannerHome}/bin/sonar-scanner -Dsonar.projectKey=train -Dsonar.projectName=train -Dsonar.sources=. -Dsonar.java.binaries=target/classes -Dsonar.sourceEncoding=UTF-8"
                 }
             }
         }
         stage("Quality Gate"){
             steps{
                 timeout(time: 30, unit: 'MINUTES'){
                    waitForQualityGate abortPipeline: true
                 }
             }
         }
    }
}
