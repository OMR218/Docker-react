pipeline {
    agent any{
        label 'docker'
    }
    stages {
        stage('Build docker image') {
            steps {
                script {
                    sh 'docker build -t omr21/docker-react/workflow/Jenkinsfile -f Dockerfile.dev .'
                }
            }
        }
        stage('Run Tests') {
            steps {
                script {
                    env.DOCKER_BUILDKIT = 1
                    sh 'docker run -e CI=true omr21/docker-react/workflow/Jenkinsfile npm test'
                }
            }
        }
    }
}