pipeline {
  agent any
  tools {
        maven 'MAVEN_HOME'
        jdk 'JAVA_HOME'
  }
  stages {
    stage('Clone repository') {
        /* Let's make sure we have the repository cloned to our workspace... */
      steps {
        checkout scm
      }
    }
    stage('Build') {
      steps {
        sh 'mvn -B -DskipTests clean package'
        sh 'echo $USER'
        sh 'echo whoami'
      }
    }
    stage('Package') {
      steps {
        sh 'serverless package'
      }
    }
    stage('Deploy') {
      steps {
        sh 'serverless deploy'
      }
    }
  }
}
