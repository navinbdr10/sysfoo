pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        echo 'compileing the code....'
        sh 'mvn compile'
      }
    }

    stage('test') {
      parallel {
        stage('test') {
          steps {
            echo 'running unit test....'
            sh 'mvn clean test'
          }
        }

        stage('testC') {
          steps {
            sleep 5
          }
        }

      }
    }

    stage('package') {
      parallel {
        stage('package') {
          steps {
            echo 'generating the artifacts....'
            sh 'mvn package -DskipTests'
            archiveArtifacts 'target/*.war'
          }
        }

        stage('testB') {
          steps {
            sleep 5
          }
        }


  }
  tools {
    maven 'Maven 3.6.3'
  }
  post {
    always {
      echo 'This pipeline is completed..'
    }

  }
}