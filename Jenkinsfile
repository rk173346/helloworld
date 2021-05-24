pipeline {

  agent any
  environment {
    //adding a comment for the commit test
    MULE_VERSION = '4.3.0'
    DEPLOY_CREDS_USR = "revanthBDR"
    DEPLOY_CREDS_PSW = "Rev@bdr1"
    BG = "BDR-Engineering"
    WORKER = "Micro"
  }
  stages {
    stage('Build') {
      steps {
            bat 'mvn -B -U -e -V clean -DskipTests package'
      }
    }


     stage('Deploy Development') {
      environment {
        APP_NAME= "helloworld-rk173346"
        ENVIRONMENT= "Sandbox"
      }
      steps {
            bat 'mvn -X -U -V -e -B -DskipTests deploy -DmuleDeploy -Dmule.version="%MULE_VERSION%" -Danypoint.username="%DEPLOY_CREDS_USR%" -Danypoint.password="%DEPLOY_CREDS_PSW%" -Dcloudhub.app="%APP_NAME%" -Dcloudhub.environment="%ENVIRONMENT%" -Dcloudhub.bg="%BG%" -Dcloudhub.worker="%WORKER%"'
      }
    }
  }

  tools {
    maven 'Maven3_6_3'
  }
}