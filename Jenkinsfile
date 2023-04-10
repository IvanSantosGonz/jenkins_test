pipeline {
    agent {
        docker { image 'node:tarampampam/17-alpine' }
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
