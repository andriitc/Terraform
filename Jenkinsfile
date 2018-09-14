pipeline {
 //agent any
 agent { label 'ec2-fleet' }
 triggers {
   pollSCM('0 1 * * *')
   //upstream(upstreamProjects: 'sonarqube', threshold: hudson.model.Result.SUCCESS)
 }

 options {
    buildDiscarder(logRotator(daysToKeepStr: '180', numToKeepStr: '100'))
    timeout(time: 1, unit: 'HOURS')
    //ansiColor('xterm')
    timestamps()
  }
  stages {
    stage('SCM') {
      steps {
        checkout([$class: 'GitSCM', \
                  branches: [[name: '*/master']], \
                  doGenerateSubmoduleConfigurations: false, \
                  extensions: [[$class: 'CloneOption', depth: 0, noTags: false, reference: '', shallow: false]], \
                  submoduleCfg: [], \
                  userRemoteConfigs: [[credentialsId: '62028f05-220e-4807-8aa4-68d01367bb96', url: 'https://github.com/andriitc/Terraform.git']]])
      }
    }
    stage("Build") {
        steps {
          wrap ([$class: 'AnsiColorBuildWrapper', 'colorMapName': 'xterm']) {
              sh 'echo something that outputs ansi colored stuff'
              sh 'sleep 20'
          }
        }
      }

  }
}
//checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: '62028f05-220e-4807-8aa4-68d01367bb96', url: 'https://github.com/andriitc/Terraform.git']]])
//checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [[$class: 'CloneOption', depth: 0, noTags: false, reference: '', shallow: false]], submoduleCfg: [], userRemoteConfigs: [[credentialsId: '62028f05-220e-4807-8aa4-68d01367bb96', url: 'https://github.com/andriitc/Terraform.git']]])
