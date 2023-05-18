pipeline {
agent any
options {
    buildDiscarder(logRotator(daysToKeepStr: '10', numToKeepStr: '10'))
    timeout(time: 12, unit: 'HOURS')
    timestamps()
}
stages {
    stage('Requirements') {
        steps {
            // MAKE SURE SCRIPT CAN BE EXECUTED DIRECTY IN A SHELL
            sh('chmod +x ./calculatePi.sh')
        }
  }
    stage('Build') {
        steps {
            // CREATE A FILE NAMED report.txt
            sh('./calculatePi.sh')
            // ARCHIVE THE REPORT
            archiveArtifacts allowEmptyArchive: true,
                artifacts: '*.txt',
                fingerprint: true,
                onlyIfSuccessful: true
             }
         }
     }
}
