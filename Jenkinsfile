pipeline {
    agent any

    environment {
        IMAGE_NAME = "nginx latest"
        TAG = "V1"
    }

   stages {

    stage ("Docker build") {
        steps {
            sh '''
        docker build -t $IMAGE_NAME:$TAG .
        '''
        }
    }

    stage ("Run_Container") {

        steps {
            sh '''
            docker run -d -p 8090:80 $IMAGE_NAME:$TAG
            '''
        }
    }

   }

   post {
    success {
        echo "from post post sucees hello"
    }
    failure {
        echo "from post failure bye "
    }
   }
}