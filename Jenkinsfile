def isSourceCodeModified = true

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
                    ).split("\n") as List
                    println diff
                    diff.removeAll { it.endsWith('.md') }
                    println diff
                    isSourceCodeModified = diff.size() > 0
                    println isSourceCodeModified
                }
            }
        }
        stage('stage 2') {
            steps {
                script {
                    println "In stage 2"
                    println isSourceCodeModified
                }
            }
        }
        stage('stage 3') {
            when {
                anyOf {
                    expression {
                        return isSourceCodeModified;
                    }
                }
                triggeredBy cause: 'UserIdCause'
            }
            steps {
                script {
                    println "In stage 3"
                    println isSourceCodeModified
                }
            }
        }
         stage('stage 4') {
            when {
                anyOf {
                    expression {
                        return isSourceCodeModified;
                    }
                }
            }
            steps {
                script {
                    println "In stage 4"
                    println isSourceCodeModified
                }
            }
        }
    }
}
