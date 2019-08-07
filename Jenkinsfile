node {
   
   stage('Code Checkout') { 
     git credentialsId: 'githubID', url: 'https://github.com/pratheep1993/maven-examples.git'
     
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
   stage('sonarqube analasyis'){
      withSonarQubeEnv(credentialsId: 'sonarid'){
    withMaven(jdk: 'JDK-1.8', maven: 'Maven-3.6.1') {
    sh 'mvn sonar:sonar -Dsonar.projectKey=pratheep1993_maven-examples -Dsonar.organization=pratheep1993 -Dsonar.host.url=https://sonarcloud.io -Dsonar.login=d85d54e4d2aae20416b0163beff1e0fadafbecb5 '
      }
      }
    }
  stage("Quality Gate"){
          timeout(time: 1, unit: 'HOURS') {
              def qg = waitForQualityGate()
              if (qg.status != 'OK') {
                  error "Pipeline aborted due to quality gate failure: ${qg.status}"
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
