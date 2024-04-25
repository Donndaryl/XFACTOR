pipeline {
    environment {
        springF = "Dockerfile-sp"
        angularF = "Dockerfile-ang"
        DOCKERHUB_CREDENTIALS=credentials('ams_cred_test') 

            }

    agent any

    stages {

        stage('Creation d\'une image ams-backend') {
            steps {
                bat 'docker build -t ams-backend ./amsBack'
            }
        }

        stage('tag and pubat image ams-backend to dockerhub') {

                    steps {

                    echo "tag and pubat image ..."

                    bat "docker tag ams-backend donndaryl/ams-backend"

                    bat "docker login -u $DOCKERHUB_CREDENTIALS_USR -p  $DOCKERHUB_CREDENTIALS_PSW"

                    bat "docker pubat donndaryl/ams-backend"

                    bat "docker logout"

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


        stage('Creation d\'une image ams-frontend') {
            steps {
                bat 'docker build -t ams-frontend ./amsFront'
            }
        }

        stage('tag and pubat image ams-frontend to dockerhub') {

                    steps {

                    echo "tag and pubat image ..."

                    bat "docker tag ams-frontend donndaryl/ams-frontend"

                    bat "docker login -u $DOCKERHUB_CREDENTIALS_USR -p  $DOCKERHUB_CREDENTIALS_PSW"

                    bat "docker pubat donndaryl/ams-frontend"

                    bat "docker logout"

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
                bat 'docker compose -f docker-compose.yml up -d'
            }
        }
    
     }

}


       
