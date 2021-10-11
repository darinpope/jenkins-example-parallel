pipeline {
  agent none
  stages {
    stage('build and run') {
      parallel {
        stage('linux-armv6') {
          agent {label 'linux-armv6'}
          stages {
            stage('build') {
              steps {
                sh 'go install dpctl'
              }
            }
            stage('run') {
              steps {
                sh 'dpctl'
              }
            }
          }
        }
        stage('linux-amd64') {
          agent {label 'linux-amd64'}
          stages {
            stage('build') {
              steps {
                sh 'go install dpctl'
              }
            }
            stage('run') {
              steps {
                sh 'dpctl'
              }
            }
            stage('unit test') {
              steps {
                sh 'echo unit test'
              }
            }
            stage('load test') {
              steps {
                sh 'echo load test'
              }
            }
            stage('deploy to storage') {
              steps {
                sh 'echo deploy to storage'
              }
            }
          }
        }      
        stage('darwin-amd64') {
          agent {label 'darwin-amd64'}
          stages {
            stage('build') {
              steps {
                sh 'go install dpctl'
              }
            }
            stage('run') {
              steps {
                sh 'dpctl'
              }
            }
            stage('unit test') {
              steps {
                sh 'echo unit test'
              }
            }
          }
        }      
      }
    }
  }
}