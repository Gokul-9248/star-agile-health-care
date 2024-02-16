pipeline{
  agent any
    stages {
      stage('checkout the code from github'){
        steps{
      git url:'https://github.com/Gokul-9248/star-agile-health-care.git'
        }
      }
      stage('building the source code'){
        steps{
      sh 'mvn compile'
        }
      }
      stage('testing the source code'){
        steps{
      sh 'mvn test'
        }
      }
      stage('package the source code'){
        steps{
      sh 'mvn clean package'
        }
      }
    }
}
