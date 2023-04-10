pipeline {
    agent {
        docker { image 'tarampampam/node:17-alpine' }
    }
    stages {
        stage('Test') {
            steps {
                sh '''
                    node --version
                    IFS=$'\'  diff_array=\\($\\(git diff HEAD~1 HEAD\\)\\)
                    echo $diff_array
                '''
            }
        }
    }
}
