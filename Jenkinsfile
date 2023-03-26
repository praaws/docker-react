pipeline {
    agent any

    stages{
        stage('Install Docker and verify version'){
            steps{
                sh 'curl -fsSL https://get.docker.com -o get-docker.sh'
                sh 'sh get-docker.sh '
                sh  'docker version'
            }

        stage('Create Docker image'){
            steps{
                sh 'docker build -t praaaws/docker-react:v1 -f Dockerfile.dev .'
            }
        }

        stage('Run Test on Docker Container'){
            steps{
                sh 'docker run praaaws/docker-react:v1 npm run test -- --coverage'
            }
        }

        }
    }
}