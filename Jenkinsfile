pipeline {
  agent any
  environment {
    PATH = "/opt/maven/bin:${PATH}"
  }
  stages {
    stage("git clone code") {
      steps{
        git 'https://github.com/chetanshell/Jenkinsbuild.git'
      }
    }
    
    stage("maven build code"){
      steps{
        sh "mvn clean install"
      }
    }
    stage("tomcat deploy code"){
      steps{
        sshagent(['ec2-user']) {
          sh "scp -o StrictHostKeyChecking=no /var/lib/jenkins/workspace/pipeline1/target/sparkjava-hello-world-1.0.war ec2-user@44.202.45.246:/opt/apache-tomcat-9.0.68/webapps"
        }
      }
    }
  }
}
