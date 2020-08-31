def runShell(String command){
    def responseCode = sh returnStatus: true, script: "${command} &> tmp.txt"
    def output =  readFile(file: "tmp.txt")
    return (output != "")
}

pipeline {
  agent any
  stages {

    stage ('Initialize') {
      steps {
        sh '''
                    python --version
                    echo "Hello world \${GIT_URL}"
            '''
      }
    }
    stage ('Check-Git-Secrets') {
      agent { label 'node-with-docker' }
      steps {
        sh 'whoami'
        sh 'rm trufflehog || true'
        sh 'docker run gesellix/trufflehog --json \${GIT_URL} > trufflehog'
        sh 'cat trufflehog'
        if (runShell('grep \'error\' trufflehog')) {
          sh "exit 1"
        }    
      }
    }
  }
}
