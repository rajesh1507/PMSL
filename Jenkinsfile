pipeline {
  agent any
  stages {

    node('node-with-docker'){
      stage ('Initialize') {
        steps {
          sh '''
                    python --version
                    echo "Hello world \${GIT_URL}"
             '''
        }
      }

      stage ('Check-Git-Secrets') {
        steps {
          sh 'whoami'
          sh 'rm trufflehog || true'
          sh 'docker run gesellix/trufflehog --json \${GIT_URL} > trufflehog'
          sh 'cat trufflehog'
        }
      }
    }
  }
}
