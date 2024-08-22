pipeline {
    agent any
    stages {
        stage('Running') {
            steps {
                checkout scm
                echo "Running ${env.BUILD_ID} on ${env.JENKINS_URL}"
            }
        }
    }
}