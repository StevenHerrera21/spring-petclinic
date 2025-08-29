#!groovy
pipeline {
  agent none
  options {
    buildDiscarder(logRotator(numToKeepStr: '5'))
    skipDefaultCheckout()
  }
  stages {
    stage('Maven Install') {
      agent {
        docker {
          image 'maven:3.8.7-eclipse-temurin-17'
          args '-u root'
          reuseNode true
        }
      }
      steps {
        ws('/var/jenkins_home/workspace/spring-petclinic-docker-clean') {
          sh 'mvn -B clean package'
        }
      }
    }
    stage('Docker Build') {
      agent any
      steps {
        sh 'docker build -t grupo04/spring-petclinic:latest .'
      }
    }
  }
}
