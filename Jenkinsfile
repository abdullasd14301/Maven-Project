pipeline { agent any
 tools { maven 'maven' }
 stages { stage('Checkout'){steps{checkout scm}} stage('Build'){steps{sh 'mvn clean compile'}} stage('Test'){steps{sh 'mvn test'}} } post { always { archiveArtifacts artifacts:'target/**/*', fingerprint:true } } }