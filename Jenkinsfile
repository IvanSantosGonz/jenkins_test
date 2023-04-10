pipeline {
    agent {
        docker { image 'tarampampam/node:17-alpine' }
    }
    stages {
        stage('Test') {
            steps {
                sh '''
                    node --version
                    IFS=$'\'  git diff --name-only $GIT_PREVIOUS_SUCCESSFUL_COMMIT $GIT_COMMIT
                    echo $diff_array
                '''
            }
        }
    }
}
