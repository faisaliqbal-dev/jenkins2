

pipeline {
  agent any
  tools {
        maven 'Maven'
    }
  stages {
    stage('test') {
      steps {
        sh 'mvn test'
      }
    }
    stage('build') {
      steps {
        sh 'mvn package'
      }
    }
    stage('deoloy on test') {
       steps{
        deploy adapters: [
            tomcat9(
                credentialsId: 'testing', 
                path: '', 
                url: 'http://13.201.89.139:8080'
            )
        ], contextPath: '/app', 
        war: '**/*.war'
       }
    }
    stage('deploy on prod') {
      steps {
        input message: 'continue ?', ok: 'yes'
        deploy adapters: [
            tomcat9(
                credentialsId: 'testing', 
                path: '', 
                url: 'http://13.126.159.208:8080/'
            )
        ], contextPath: '/app', 
        war: '**/*.war'
      }
    }
  }
}
