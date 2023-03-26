pipeline {
    agent any

    triggers{
        githubPush()
    }

    stages{
        stage('enable docker'){
            steps{
                sh 'sudo chmod 777 /var/run/docker.sock'
            }
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