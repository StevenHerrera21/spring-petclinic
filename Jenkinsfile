#!groovy 
pipeline { 
  agent none 
  stages { 
    stage('Maven Install') { 
      agent { 
        docker { 
          image 'maven:3.8.7-eclipse-temurin-17'
          args '-u root'
        }   
      }   
      steps { 
        sh 'mvn clean install' 
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
