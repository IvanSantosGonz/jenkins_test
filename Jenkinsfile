pipeline {
    agent {
        docker { image 'tarampampam/node:17-alpine' }
    }
    stages {
        stage('Test') {
            steps {
                script {
                   def diff = sh (
                        script: 'git diff --name-only $GIT_PREVIOUS_SUCCESSFUL_COMMIT $GIT_COMMIT',
                        returnStdout: true
                    )
                    println diff
                    def list = diff.split("\n") as List
                    println list
                    list.removeAll { it.endsWith('.md') }
                    println list
                    def result = list.size() > 0
                    println result
                }
            }
        }
    }
}
