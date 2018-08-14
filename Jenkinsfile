node {
  ansiColor ('xterm') {
    stage ('Color') {
      writeFile file: "usefulfile.txt", text: "This file is useful, need to archive it."
    }
    stage('Archive') {
      archiveArtifacts artifacts: '*.txt', excludes: '*.md'
    }
  }
}
