pipeline {
    agent any
    stages {
        // stage('Checkout') {
        //     steps {
        //         git 'https://github.com/hoanglinhdigital/nodejs-random-color.git'
        //     }
        // }

        stage('Build') {
            steps {
                sh 'docker build -t jenkins-node-project:ver-${BUILD_ID} .'
            }
        }
        stage('Upload image to ECR') {
            steps {
                sh 'aws ecr get-login-password --region ap-southeast-1 | docker login --username AWS --password-stdin 430950558682.dkr.ecr.ap-southeast-1.amazonaws.com'
                sh 'docker tag jenkins-node-project:ver-${BUILD_ID} 430950558682.dkr.ecr.ap-southeast-1.amazonaws.com/jenkins-node-project:ver-${BUILD_ID}'
                sh 'docker push 767397964075.dkr.ecr.ap-southeast-1.amazonaws.com/jenkins-node-project:ver-${BUILD_ID}'
            }
        }
    }
}
