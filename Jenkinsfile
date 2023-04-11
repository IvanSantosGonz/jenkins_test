def isSourceCodeModified = true

def isSourceCodeModified2() {
    def diff = sh(
            script: 'git diff --name-only $GIT_PREVIOUS_SUCCESSFUL_COMMIT $GIT_COMMIT',
            returnStdout: true
    ).split("\n") as List
    println diff
    diff.removeAll { it.endsWith('.md') }
    println diff
    return diff.size() > 0
}

pipeline {
    agent {
        docker { image 'tarampampam/node:17-alpine' }
    }
    stages {
        stage('Test') {
            steps {
                script {
                    isSourceCodeModified2()
                }
            }
        }
        stage('stage 2') {
            steps {
                script {
                    println "In stage 2"
                    println isSourceCodeModified2()
                }
            }
        }
        stage('stage 3') {
            when {
                anyOf {
                    expression {
                        return isSourceCodeModified;
                    }
                    triggeredBy cause: 'UserIdCause'
                }
            }
            steps {
                script {
                    println "In stage 3"
                    println isSourceCodeModified2()
                }
            }
        }
        stage('stage 4') {
            when {
                anyOf {
                    expression {
                        return isSourceCodeModified2();
                    }
                }
            }
            steps {
                script {
                    println "In stage 4"
                    println isSourceCodeModified()
                }
            }
        }

    }
}
