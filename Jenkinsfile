pipeline {
    agent {
        docker { image 'node:16.13.1-alpine' }
    }
    stages {
        stage('Test') {
            steps {
                sh '''
                    node --version
                    IFS=$'\'  diff_array=($(git diff HEAD~1 HEAD))
                '''
            }
        }
    }
}
