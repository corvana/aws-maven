#!/usr/bin/env groovy

// Use the default version of the jenkins-pipelines plugin
@Library("corvana-jenkins-pipelines") _

pods.standard {
  checkout scm

  stage('Build') {
    mvn("clean verify -DskipTests=true", 'pom.xml')
  }

  if (currentBuild.result == null || currentBuild.result == 'SUCCESS') {
    stage('Deploy') {
      mvn('deploy -DskipTests=true', 'pom.xml', null)
    }
  }
}

