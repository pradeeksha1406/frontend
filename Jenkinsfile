pipeline{
  agent { label 'workstation'}

  stages {

    stage('Code Quality'){
     when {
        allOf {
            branch 'main'
            expression { env.TAG_NAME != env.BRANCH_NAME }
        }
     }
      steps {
        sh 'sonar-scanner -Dsonar.host.url=http://sonarqube.techadda.co:9000 -Dsonar.login=admin -Dsonar.password=admin123 -Dsonar.projectKey=frontend -Dsonar.qualitygate.wait=true'
      }
    }


    stage('Release'){
     when {
             expression { env.TAG_NAME ==~ env.BRANCH_NAME }
              }
      steps {
//        sh 'docker build -t 851725420695.dkr.ecr.us-east-1.amazonaws.com/frontend:${TAG_NAME} .'
//        sh 'aws ecr get-login-password --region us-east-1 | docker login --username AWS --password-stdin 851725420695.dkr.ecr.us-east-1.amazonaws.com'
//        sh 'docker push 851725420695.dkr.ecr.us-east-1.amazonaws.com/frontend:${TAG_NAME}'
       echo 'CI'
        }
     }
  }
}




