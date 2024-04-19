pipeline{
  agent { label 'workstation'}

  stages {

    stage('Code Quality'){
      steps {
        sh 'sonar-scanner -Dsonar.host.url=http://sonarqube.techadda.co:9000 -Dsonar.login=admin -Dsonar.password=admin123 -Dsonar.projectKey=frontend -Dsonar.qualitygate.wait=true'
      }
    }

    stage('Release'){
     when {
        expression { TAG_NAME ==~ ".*" }

         }
      steps {
       sh 'env'
        echo 'CI'
      }
    }
  }
}

