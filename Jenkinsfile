pipeline {
 agent any
//  agent { lable 'ec2-fleet' }
 triggers {
   pollSCM('0 1 * * *')
 }
 options {
    buildDiscarder(logRotator(daysToKeepStr: '180', numToKeepStr: '100')) \
    //timeout(time: 1, unit: 'HOURS') \
    //@ansiColor('xterm') \
    timestamps()
  }
  stages {
    stage('SCM') {
      steps {
        checkout([$class: 'GitSCM', \
                  branches: [[name: '*/master']], \
                  checkout([$class: 'GitSCM', \
                  doGenerateSubmoduleConfigurations: false, \
                  extensions: [[$class: 'CloneOption', depth: 0, noTags: false, reference: '', shallow: false]], \
                  submoduleCfg: [], \
                  userRemoteConfigs: [[credentialsId: '62028f05-220e-4807-8aa4-68d01367bb96', url: 'https://github.com/andriitc/Terraform.git']]])
      }
    }
    stage("Test Color") {
        steps {
          wrap ([$class: 'AnsiColorBuildWrapper', 'colorMapName': 'xterm']) {
              sh 'echo something that outputs ansi colored stuff'
          }
        }
      }

  }
}
//checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: '62028f05-220e-4807-8aa4-68d01367bb96', url: 'https://github.com/andriitc/Terraform.git']]])
//checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [[$class: 'CloneOption', depth: 0, noTags: false, reference: '', shallow: false]], submoduleCfg: [], userRemoteConfigs: [[credentialsId: '62028f05-220e-4807-8aa4-68d01367bb96', url: 'https://github.com/andriitc/Terraform.git']]])
