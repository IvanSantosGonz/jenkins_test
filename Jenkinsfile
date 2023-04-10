pipeline {
    agent {
        docker { image 'tarampampam/node:17-alpine' }
    }
    stages {
        stage('Test') {
            steps {
                script {
                   GIT_COMMIT_EMAIL = sh (
                        script: 'git --no-pager show -s --format=\'%ae\'',
                        returnStdout: true
                    ).trim()
                    echo "Git committer email: ${GIT_COMMIT_EMAIL}"
                }
                sh '''
                    node --version
                    IFS=$'\n'
                    git diff --name-only $GIT_PREVIOUS_SUCCESSFUL_COMMIT $GIT_COMMIT
                    echo $diff_array[1]
                    # Print each line of the diff array
                    number=0
                    for line in "${diff_array[@]}"
                    do
                      if [[ $line != *.md ]]
                      then
                        \\(\\(number++\\)\\)
                      fi
                    done
                    echo $number
                '''
            }
        }
    }
}
