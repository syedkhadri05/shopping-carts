pipeline {
  agent none
  stages {
    stage('build') {
      agent {
        docker {
          image 'lagairogo/carts-maven'
        }

      }
      steps {
        echo 'this is the first job'
        sh 'mvn compile'
      }
    }

    stage('test') {
      agent {
        docker {
          image 'lagairogo/carts-maven'
        }

      }
      steps {
        echo 'this is the second job'
        sh 'mvn test'
      }
    }

    stage('package') {
      agent {
        docker {
          image 'lagairogo/carts-maven'
        }

      }
      steps {
        echo 'this is the third job'
        sh 'mvn package'
      }
    }

    stage('Archive') {
      agent {
        dockerfile {
          filename 'lagairogo/carts-maven'
        }

      }
      steps {
        archiveArtifacts '**/target/*.jar'
      }
    }

    stage('Build and Publish') {
      steps {
        script {
          docker.withRegistry('https://index.docker.io/v1/', 'dockerlogin') {
            def dockerImage = docker.build("syedkhadri05/shopping-carts:v${env.BUILD_ID}", "./")
            dockerImage.push()
            dockerImage.push("latest")
          }
        }

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