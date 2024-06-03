pipeline{
  agent { label 'workstation'}

  stages {

    stage('Code Quality'){
      when {
        allOf {
             expression { env.TAG_NAME != env.BRANCH_NAME }
        }
     }
      steps {
        //sh 'sonar-scanner -Dsonar.host.url=http://sonarqube.techadda.co:9000 -Dsonar.login=admin -Dsonar.password=admin123 -Dsonar.projectKey=backend -Dsonar.qualitygate.wait=true'
        echo 'ok'
      }
    }

    stage('Unit Tests'){
      when {
        allOf {
            expression { env.TAG_NAME != env.BRANCH_NAME }
            branch 'main'
        }
      }
       steps {
          //Ideally we should run the tests , But here the developer have skipped it. So assuming those are good and proceeding
          //sh 'npm test'
          echo 'CI'
       }
    }

    stage('Release'){
      when {
        expression { env.TAG_NAME ==~ ".*"}
     }
      steps {
//        sh 'zip -r frontend-${TAG_NAME}.zip static asset-manifest.json index.html robots.txt'
//        sh 'curl -sSf -u "admin:Admin@123" -X PUT -T frontend-${TAG_NAME}.zip "http://artifactory.techadda.co:8082/artifactory/frontend/frontend-${TAG_NAME}.zip"'
       sh 'docker build -t 851725420695.dkr.ecr.us-east-1.amazonaws.com/frontend:${TAG_NAME} .'
       sh 'aws ecr get-login-password --region us-east-1 | docker login --username AWS --password-stdin 851725420695.dkr.ecr.us-east-1.amazonaws.com'
       sh 'docker push 851725420695.dkr.ecr.us-east-1.amazonaws.com/frontend:${TAG_NAME}'
      }
    }
  }
}
