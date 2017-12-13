#!/usr/bin/env groovy
// see https://jenkins.io/doc/book/pipeline/syntax/

pipeline {

    agent any

    stages {
        stage("Execute tests") {
            steps {
                ansiColor("xterm") {
                    sh "./gradlew check"
                }
            }
            post {
                always {
                    junit "build/test-results/test/TEST-*.xml"
                }
            }
        }
    }

    post {
        always {
            deleteDir()
        }

        success {
            echo "SUCCESS!"
        }

        failure {
            echo "FAILURE!"
        }

        unstable {
            echo "FAILING TESTS!"
        }
    }
}
