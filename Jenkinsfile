pipeline {
    agent {
        node {
            label 'built-in'
        }
    }
    stages {
          stage('test') {
            when {
                branch 'main'
            }
            steps {

                sh "echo 'pepe'"
            }
          }
    }
}
