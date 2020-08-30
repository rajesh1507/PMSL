pipeline {
  agent any
  tools {
    python3 'Python3'
  }
  stages {

    stage ('Initialize') {
      steps {
        sh '''
                    echo "${python3 --version}"
                    echo "Hello world"
            '''
      }
    }
  }
}
