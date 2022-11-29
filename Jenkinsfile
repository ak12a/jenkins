pipeline {
    agent any
    stages{
        stage("maven build artifacts"){
            steps{
                sh "mvn clean package -DskipTests=true" // Bulding package and achiving the artificats 
                archive 'target/*.jar'
            }
        }
        stage("Unit Tests - JUnit and Jacoco'"){
            steps{
                sh "mvn test"  
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml'
                    jacoco execPattern: 'target/jacoco.exec'

                }
            }
        }
    }
}

