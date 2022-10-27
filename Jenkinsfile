pipeline {

    agent any

  

    stages {

        stage('Build') {

            steps {

                echo "Build_stage"

                sh 'DOCKER_BUILDKIT=1 docker build -t tzivya/todo-be:latest -f Dockerfile-pipeline --target builder .'

            }

        }





        stage('Delivery') {

            steps {

                echo "Delivery_stage"

                sh 'DOCKER_BUILDKIT=1 docker build -t tzivya/todo-be:latest -f Dockerfile-pipeline --target delivery .'

            }

        }
        
        
        
         stage('Cleanup') {

            steps {

                echo "Cleanup_stage"

                sh 'docker system prune -f'

            }

        }
        stage('Push') {

            steps {

                echo "Push_stage"
                sh 'docker login -u ${username} -p ${password}'
                sh 'docker push tzivya/todo-be:latest'

            }

        }

    }

}
