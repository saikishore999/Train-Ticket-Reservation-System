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
    }
}