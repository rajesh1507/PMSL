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
  }
}
