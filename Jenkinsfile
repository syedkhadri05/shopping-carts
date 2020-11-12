pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        echo 'this is the first job'
        sh 'mvn compile'
      }
    }

    stage('test') {
      steps {
        echo 'this is the second job'
        sh 'mvn test'
      }
    }

    stage('package') {
      steps {
        echo 'this is the third job'
        sh 'mvn package'
      }
    }

    stage('Archive') {
      steps {
        archiveArtifacts '**/target/*.jar'
      }
    }

  }
  tools {
    maven 'maven'
  }
  post {
    always {
      echo 'this pipeline has completed...'
    }

  }
}