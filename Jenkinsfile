#!groovy 
pipeline {
  agent none
  stages {
    stage('Maven Install') {
      agent {
        docker {
          image 'maven:3.8.7-eclipse-temurin-17'
          reuseNode true
        }
      }
      steps {
        sh 'mvn -B clean package'
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
