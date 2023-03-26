pipeline {
    agent any

    triggers{
        githubPush()
    }

    stages{

        stage('Create Docker image'){
            steps{
                script{
                    docker.build('praaaws/docker-react:v1', '-f Dockerfile.dev .')
                }
            }
        }

        stage('Run Test on Docker Container'){
            steps{
                sh 'docker run praaaws/docker-react:v1 npm run test -- --coverage'
            }
        }

        }
    }