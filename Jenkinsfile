pipeline {
  agent any
  tools{
    maven 'Maven 3.6.3'
    }
  }
  stages{
      stage("build"){
          steps{
              echo 'compileing the code....'
              sh 'mvn compile'
          }
      }
      stage("test"){
          steps{
              echo 'running unit test....'
              sh 'mvn clean test'
          }
      }
      stage("package"){
          steps{
              echo 'generating the artifacts....'
              sh 'mvn package -DskipTests'
          }
      }
  }

  post{
    always{
        echo 'This pipeline is completed..'
    }
  }
}