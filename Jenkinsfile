pipeline {
agent any
stages {
stage('Build Application') {
steps {
echo 'Application is in Building Phase'
bat 'mvn clean install'
}
}
stage('Test Application') {
steps {
echo 'Application is in Testing Phase'
bat 'mvn test'
}
}
    stage('Deploy CloudHub') { 
      environment {
        ANYPOINT_CREDENTIALS = credentials('anypointplatform')
      }
      steps {
        bat 'mvn clean package deploy -Denv=dev -Dmule.key=SecureP@ss -Dusername=${ANYPOINT_CREDENTIALS_USR} -Dpassword=${ANYPOINT_CREDENTIALS_PSW} -Dapplicationname=cicd-appdev-practice2 -Dmule.version=4.3.0 -Denvironment=Sandbox -DmuleDeploy'
      
      }
    }
}
}