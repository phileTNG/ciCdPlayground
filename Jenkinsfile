pipeline {
    agent any

    tools {
        nodejs 'yarn'
    }

    stages {
        stage('Build') {
            steps {
                // Get some code from a GitHub repository
                git 'https://github.com/phileTNG/ciCdPlayground'
                git branch: 'main', url: 'https://github.com/phileTNG/ciCdPlayground.git'

                // Run Maven on a Unix agent.
                sh 'yarn install'
                sh 'yarn build'
                sh 'yarn test'

            }

            post {
                // If Maven was able to run the tests, even if some of the test
                // failed, record the test results and archive the jar file.
                success {
                    junit '*/reports/**/*.xml'
                }
            }
        }
    }
}
