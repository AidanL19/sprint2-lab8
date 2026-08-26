pipeline {
  agent any
  stages {
    stage('Checkout') { steps { checkout scm } }
    stage('Compile') {
      steps { sh 'mvn -B package' }
    }
    stage('Build Image') {
      steps { sh 'docker build -t team-skeleton:${BUILD_NUMBER} .' }
    }
    stage('Test') {
      steps { sh 'mvn -B test' }
      post { always { junit 'target/surefire-reports/*.xml' } }
    }
  }
}
