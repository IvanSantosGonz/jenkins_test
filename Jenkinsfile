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
                    # Print each line of the diff array
                    number=0
                    for line in "${diff_array[@]}"
                    do
                      if [[ $line != *.md ]]
                      then
                        echo $number
                      fi
                    done
                    echo $number
                '''
            }
        }
    }
}
