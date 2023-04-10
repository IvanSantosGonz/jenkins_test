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
            steps {

                sh "echo 'pepe'"
            }
          }
    }
}
