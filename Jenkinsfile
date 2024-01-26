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

                // Run Maven on a Unix agent.
                sh 'yarn install'
                sh 'yarn build'
                sh 'yarn test'

                // To run Maven on a Windows agent, use
                // bat "mvn -Dmaven.test.failure.ignore=true clean package"
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
