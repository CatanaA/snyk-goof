pipeline {
  agent any

  stages {
    stage('Checkout') {
      steps {
        checkout([$class: 'GitSCM', branches: [[name: '*/master']],
          userRemoteConfigs: [[credentialsId: 'GitHub_token', url: 'https://github.com/CatanaA/snyk-goof.git']]])
          sh "ls -lart ./*"
            }
          }

    stage('Build') {
      steps {
        println "Starting Snyk"
        sh 'npm install -g' 
        snykSecurity(snykTokenId: 'Alexandra_Snyk_token', snykInstallation: 'Snyk_test')
            
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