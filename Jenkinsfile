pipeline {
    agent {
        docker { image 'tarampampam/node:17-alpine' }
    }
    stages {
        stage('Test') {
            steps {
                script {
                   GIT_DIFF = sh (
                        script: 'git diff --name-only $GIT_PREVIOUS_SUCCESSFUL_COMMIT $GIT_COMMIT',
                        returnStdout: true
                    ).split("\n")
                    echo "GIT_DIFF: ${GIT_DIFF}"
                }

            }
        }
    }
}
