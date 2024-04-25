pipeline {
    environment {
        springF = "Dockerfile-sp"
        angularF = "Dockerfile-ang"
        DOCKERHUB_CREDENTIALS=credentials('ams_cred_test') 

            }

    agent any

    stages {

        stage('Création d\'une image ams-backend') {
            steps {
                sh 'docker build -t ams-backend ./backend'
            }
        }

        stage('tag and push image ams-backend to dockerhub') {

                    steps {

                    echo "tag and push image ..."

                    sh "docker tag ams-backend donndaryl/ams-backend"

                    sh "docker login -u $DOCKERHUB_CREDENTIALS_USR -p  $DOCKERHUB_CREDENTIALS_PSW"

                    sh "docker push donndaryl/ams-backend"

                    sh "docker logout"

                    }

               post{

                    success{
                         echo "====++++success++++===="
                         }

                    failure{
                         echo "====++++failed++++===="
                         }
          
        
               }
        }


        stage('Création d\'une image ams-frontend') {
            steps {
                sh 'docker build -t ams-frontend ./frontend'
            }
        }

        stage('tag and push image ams-frontend to dockerhub') {

                    steps {

                    echo "tag and push image ..."

                    sh "docker tag ams-frontend donndaryl/ams-frontend"

                    sh "docker login -u $DOCKERHUB_CREDENTIALS_USR -p  $DOCKERHUB_CREDENTIALS_PSW"

                    sh "docker push donndaryl/ams-frontend"

                    sh "docker logout"

                    }

               post{

                    success{
                         echo "====++++success++++===="
                         }

                    failure{
                         echo "====++++failed++++===="
                         }
          
        
               }
        }

        stage('Docker-compose') {
            steps {
                sh 'docker compose -f docker-compose.yml up -d'
            }
        }
    
     }

}


       
