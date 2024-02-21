pipeline{
    agent any
    stages{
        stage('checkout the code from github'){
            steps{
                 git url: 'https://github.com/Gokul-9248/star-agile-health-care.git', branch:"master"
                 echo 'github url checkout'
            }
        }
        stage('codecompile'){
            steps{
                echo 'starting compiling'
                sh 'mvn compile'
            }
        }
        stage('codetesting'){
            steps{
                sh 'mvn test'
            }
        }
        stage('qa'){
            steps{
                sh 'mvn checkstyle:checkstyle'
            }
        }
        stage('package'){
            steps{
                sh 'mvn package'
            }
        }
         
         
         stage('run dockerfile'){
          steps{
               sh 'docker build -t gokul1311/medicure:1.0 .'
           }
         }

         stage('Docker login') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerhub-pwd', passwordVariable: 'PASS', usernameVariable: 'USER')]) {
                    sh "echo $PASS | docker login -u $USER --password-stdin"
                    sh 'docker push gokul1311/medicure:1.0'
                }
            }
        }
         
         stage('port expose and container creation'){
          steps{
               sh 'docker run -itd -p 80:8082 --name container1 gokul1311/medicure:1.0'
           }
         }
         
    }
}
