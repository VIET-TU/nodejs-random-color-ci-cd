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
                sh 'docker build -t nodejs-random-color:latest .'
            }
        }
        stage('Upload image to ECR') {
            steps {
                sh 'aws ecr get-login-password --region ap-southeast-1 | docker login --username AWS --password-stdin 287925497349.dkr.ecr.ap-southeast-1.amazonaws.com'
                sh 'docker tag nodejs-random-color:latest 287925497349.dkr.ecr.ap-southeast-1.amazonaws.com/nodejs-random-color:latest'
                sh 'docker push 287925497349.dkr.ecr.ap-southeast-1.amazonaws.com/nodejs-random-color:latest'
            }
        }
    }
}
