pipeline {
  agent any
//  agent { lable 'ec2-fleet' }
/*  options {
    @buildDiscarder(logRotator(daysToKeepStr: '180', numToKeepStr: '100')) \
    @pipelineTriggers([upstream('Terraform/master, '), pollSCM('0 1 * * *')]) \
    //timeout(time: 1, unit: 'HOURS') \
    @ansiColor('xterm') \
    @timestamps()
          }
*/
  tools {
    gradle "Gradle"
  }

  try {
        timeout(time: 1, unit: 'HOURS') {
          stages {
            stage ("SCM") {
              steps {
                      	checkout([$class: 'GitSCM', branches: [[name: '*/master']], \
                         doGenerateSubmoduleConfigurations: false, \
                         extensions: [[$class: 'CloneOption', depth: 0, noTags: false, reference: '', shallow: false]], \
                         submoduleCfg: [], \
                         userRemoteConfigs: [[credentialsId: '62028f05-220e-4807-8aa4-68d01367bb96', \
                         url: 'https://github.com/andriitc/Terraform.git']]])
                    }
                  }
              stage ("Color") {
                writeFile file: "usefulfile.txt", text: "This file is useful, need to archive it."
              }
              stage("Archive") {
                archiveArtifacts artifacts: '*.txt', excludes: '*.md'
                sh "ls -la"
            }

        }
      }
    }
    catch(err) {
      echo "This Job has been Aborted"
    }
}
