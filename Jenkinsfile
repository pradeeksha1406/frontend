pipeline{
  agent { label 'workstation'}

  stages {

    stage('Code Quality'){
      steps {
        sh 'sonar-scanner -Dsonar.host.url=http://34.204.5.63:9000 -Dsonar.login=admin -Dsonar.password=admin123 -Dsonar.projectKey=backend -Dsonar.qualitygate.wait=true'
      }
    }

    stage('Release'){
      steps {
        echo 'CI'
      }
    }
  }
}

