pipeline {
    agent any
    stages {
        //stage('Checkout') {
          //  steps {
             //   git 'https://github.com/tridung1109/nodejs-random-color.git'
          //  }
       // }

        stage('Build') {
            steps {
                sh 'docker build -t nodejs-random-color-private:ver-${BUILD_ID} .'
            }
        }
        stage('Upload image to ECR') {
            steps {
                sh 'aws ecr get-login-password --region ap-southeast-1 | docker login --username AWS --password-stdin 126623035473.dkr.ecr.ap-southeast-1.amazonaws.com'
                sh 'docker tag nodejs-random-color-private:ver-${BUILD_ID} 126623035473.dkr.ecr.ap-southeast-1.amazonaws.com/nodejs-random-color-private:ver-${BUILD_ID}'
                sh 'docker push 126623035473.dkr.ecr.ap-southeast-1.amazonaws.com/nodejs-random-color-private:ver-${BUILD_ID}'
            }
        }
    }
}
