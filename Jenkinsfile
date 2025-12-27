pipeline {
    agent any

    environment {
        IMAGE_NAME="Jenkins_nginx"
        TAG="V1"
        CONTAINER_NAME="Jenkins_nginx_container"

    }

    stages {

        stage ("Checkout") {
            steps {
                echo "Code already checkedout by SCM"
            }
        }

        stage ("Docker_build") {
            steps {
                sh '''
                docker build -t $IMAGE_NAME:$TAG
                '''
            }

        }

        stage ("Run_container") {
            steps {
                sh '''
                docker rm -f $CONTAINER_NAME || true
                docker build -d --name $CONTAINER_NAME -p 8090:80 $IMAGE_NAME:$TAG
                '''
            }

        }


    }

    post {
        success {
            echo "build success messages from post"
        }
        failure {
            echo "build failed from post"
        }
        always {
            echo "this runs always"
        }
    }
}