pipeline {
    agent {
        node {
            label 'built-in'
        }
    }
    stages {
          stage('test') {
            when {
                branch 'master'
            }
            sh "echo 'pepe'"

          }
    }
}
