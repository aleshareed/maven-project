pipeline {
  /* A Declarative pipeline*/
  agent any

  stages {
    stage('Build'){
      steps {
        bat 'mvn clean package'
      }
      post {
        success {
          echo 'Now Archiving...'
          archiveArtifacts artifacts: '**/target/*.war'
        }
      }
    }
    stage('deploy to staging'){
      steps {
        build job: 'deploy-to-staging'
      }
    }
  }
}
