pipeline {
  agent any
  stages {
    stage('Compile') {
      steps{
        sh 'mvn clean compile'
      }
    }

    stage('UnitTest') {
      steps{
        sh 'mvn clean test'
      }
    }
    
    stage('Package') {
      steps{
        sh 'mvn package'
     }
    }
    stage('Cont_Deploy') {
      steps{
        deploy adapters: [tomcat9(credentialsId: 'Tomcat', path: '', url: 'http://172.31.20.27:9090/calculator')], contextPath: null, war: '**/*.war'
      }
    }
  }
}

