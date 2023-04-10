pipeline {
    agent {
        docker { image 'tarampampam/node:17-alpine' }
    }
    stages {
        stage('Test') {
            steps {
                sh '''
                    node --version
                    git diff HEAD\\~1 HEAD
                '''
            }
        }
    }
}
