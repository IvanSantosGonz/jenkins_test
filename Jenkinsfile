def haveBeenSourceCodeModified = false

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
                    )split("\n") as List
                    println diff
                    diff.removeAll { it.endsWith('.md') }
                    println diff
                    def haveBeenSourceCodeModified = diff.size() > 0
                    println haveBeenSourceCodeModified
                }
            }
        }
        stage('stage 2') {
            steps {
                script {
                    println "In stage 2"
                    println haveBeenSourceCodeModified
                }
            }
        }
    }
}
