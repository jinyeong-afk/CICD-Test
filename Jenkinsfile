pipeline {
    agent any
    options {
        timeout(time: 1, unit: 'HOURS')
    }
    environment {
        SOURCECODE_JENKINS_CREDENTIAL_ID = 'jenking-github-wh'
        SOURCE_CODE_URL = 'https://github.com/jinyeong-afk/CICD-Test.git'
        RELEASE_BRANCH = 'master'
    }
    stages {

        stage('clone') {
            steps {
                git url: "$SOURCE_CODE_URL",
                    branch: "$RELEASE_BRANCH",
                    credentialsId: "$SOURCECODE_JENKINS_CREDENTIAL_ID"
                sh "ls -al"
            }
        }

        stage('dockerizing') {
            steps {
                   sh "pwd"
                   sh "gradle clean"
                   sh "gradle bootJar"

                   sh "docker build -t CICD-Test ."
            }
        }

        stage('deploy') {
            steps {
                sh '''

                  docker run -d -p 8080:8080 CICD-Test
                '''
            }
        }
    }
}