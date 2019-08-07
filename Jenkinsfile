node {
   
   stage('Code Checkout') { 
     git credentialsId: 'githubID', url: 'https://github.com/pratheep1993/maven-examples'
     
    }
   stage('Build') {
    withMaven(jdk: 'JDK-1.8', maven: 'Maven-3.6.1') {
      sh 'mvn clean compile'
      }
    }
   stage('Unit Test run') {
    withMaven(jdk: 'JDK-1.8', maven: 'Maven-3.6.1') {
     sh 'mvn test'
      } 
    }
   stage('Sonarqube analysis'){
   withSonarQubeEnv(credentialsId: 'sonarid') {
    withMaven(jdk: 'JDK-1.8', maven: 'Maven-3.6.1') {
    sh 'mvn sonar:sonar -Dsonar.projectKey=pratheep1993_maven-examples -Dsonar.organization=pratheep1993 -Dsonar.host.url=https://sonarcloud.io -Dsonar.login=81fdeebd68a9cc1389cd170cf5405664a79f5388 ' 
      }
     }
    }
  stage("Quality Gate"){
          timeout(time: 1, unit: 'HOURS') {
              def qg = waitForQualityGate()
              if (qg.status != 'OK') {
          
              }
          }
    }
   stage('Package to Jfrog') {
    withMaven(jdk: 'JDK-1.8', maven: 'Maven-3.6.1') {
     sh 'mvn package'
      }
    }
   
   stage('Deploy to Dev') {
     
    }
   stage('Automation Testing') {
     
    }
   stage('Deploy to Test') {
     
    }
   stage('Smoke Testing') {
     
    }
   stage('Deploy to Prod') {
     
    }
   stage('Acceptance Testing') {
     
    }
}
