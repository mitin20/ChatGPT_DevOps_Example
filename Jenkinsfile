pipeline {
    agent any
    stages {
        stage('Build image & Push to Dockerhub') {
            steps {
                script {
                    // Log into dockerhub 
                    sh "echo ${DOCKER_PASSWPRD} | docker login --username ${DOCKER_USERNAME} --password-stdin"
                }
            }
            steps {
                // Build docker image
                sh 'docker build -t mitin20/chatgpt_devops_example:$BUILD_ID .'
            }
            steps {
                // Push image to Dockerhub
                sh 'docker push mitin20/chatgpt_devops_example:$BUILD_ID'
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                // create config from base64 string
                script {
                    sh 'echo "${KUBECONFIG_BASE64}" | base64 -d > config'
                }

                // Apply deployment
                sh 'KUBECONFIG=./config kubectl apply -f deployment.yml'

            }
        }
    }
}
