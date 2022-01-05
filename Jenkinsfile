pipeline {
  agent any

  stages {
    stage('Checkout') {
      steps {
        checkout([$class: 'GitSCM', branches: [[name: '*/branchname']],
          userRemoteConfigs: [[credentialsId: 'GitHub_token', url: 'https://github.com/CatanaA/snyk-goof.git']]])
          sh "ls -lart ./*"
            }
          }

    stage('Build') {
      steps {
        snykSecurity(snykTokenId: '	Alexandra_Snyk_token', snykInstallation: 'Snyk_test'){
          sh 'npm install -g'  
        }
        
      }
    }
    stage('Docker Build'){
      steps{
        script{
          sh "docker-compose up --build"
          //sh "docker-compose down"
        }
      }
    }
  }
}