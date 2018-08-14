pipeline {
  agent { lable 'ec2-fleet' }
  options {
    buildDiscarder(logRotator(daysToKeepStr: '180', numToKeepStr: '100')), \
    pipelineTriggers([upstream('Terraform/master, '), pollSCM('0 1 * * *'), \
    timeout(time: 1, unit: 'HOURS'), \
    ansiColor('xterm'), \
    timestamps() 
  }
  tools {
    gradle "gradle"
  }
  stages {
    stage ('SCM') {
      steps {
	checkout([$class: 'GitSCM', branches: [[name: '*/master']], \
                 doGenerateSubmoduleConfigurations: false, \
                 extensions: [[$class: 'CloneOption', depth: 0, noTags: false, reference: '', shallow: false]], \
                 submoduleCfg: [], \
                 userRemoteConfigs: [[credentialsId: '62028f05-220e-4807-8aa4-68d01367bb96', \
                 url: 'https://github.com/andriitc/Terraform.git']]])
            }
                 }

    stage('Gradle') {
      steps {
	sh 'gradle '
                 }
      }
    }
  }
}
