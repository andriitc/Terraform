pipeline {
  agent any
  stages {
    stage('SCM') {
      steps {
        git(url: 'https://github.com/andriitc/Terraform.git', branch: 'master', credentialsId: '62028f05-220e-4807-8aa4-68d01367bb96')
      }
    }
  }
}