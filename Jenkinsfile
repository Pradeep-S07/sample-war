pipeline {
   agent any
   stages {
      stage('maven version'){
         sh 'mvn -v'
      }
      stage('Testing') {
         sh 'mvn clean test'
      }
         
   }
}
   
