pipeline {
    agent any 
    stages {
        stage('Compile and Clean') { 
            steps {
                // Run Maven on a Unix agent.
              
                sh "mvn clean compile"
            }
        }
        stage('deploy') { 
            
            steps {
                sh "mvn package"
            }
        }
        stage('Build Docker image'){
          
            steps {
                echo "Hello Vageesh"
                sh 'ls'
                sh 'sudo docker build -t  vageesh7795/docker_jenkins_springboot:${BUILD_NUMBER} .'
            }
        }
        stage('Docker Login'){
            
            steps {
                 
                    sh "sudo docker login -u vageesh7795 -p Vageesh@12"
                
            }                
        }
        stage('Docker Push'){
            steps {
                sh 'sudo docker push vageesh7795/docker_jenkins_springboot:${BUILD_NUMBER}'
            }
        }
        stage('Docker deploy'){
            steps {
               
                sh 'sudo docker run -itd -p  8081:8080 vageesh7795/docker_jenkins_springboot:${BUILD_NUMBER}'
            }
        }
        stage('Archving') { 
            steps {
                 archiveArtifacts '**/target/*.jar'
            }
        }
    }
}

