pipeline{

    agent any

// uncomment the following lines by removing /* and */ to enable
   tools{
       maven 'maven' 
    }  
    stages{
        stage('build'){
            steps{
                echo 'this is the first job'
                sh 'mvn compile'
            }
        }
        stage('test'){
            steps{
                echo 'this is the second job'
                sh 'mvn test'
            }
        }
        stage('package'){
            steps{
                echo 'this is the third job'
                sh 'mvn package'
            }
        }
    }
    
    post{
        always{
            echo 'this pipeline has completed...'
        }
        
    }   
}
