pipeline {
  agent any
    stages {
    stage('Syntax Check') {
      parallel {
        stage('OpenModelica') {
          agent {
            docker {
              image 'openmodelica/openmodelica:nightly'
            }
          }
          steps {
            sh 'omc .CI/check.mos'
          }
        }
        stage('moparser') {
          agent {
            docker {
              image 'openmodelica/moparser'
            }
          }
          steps {
            sh 'moparser -r -v 2.2 BioChem'
          }
        }
      }
    }
  }
}
