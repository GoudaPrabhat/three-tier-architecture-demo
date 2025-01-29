pipeline {
    agent any
    stages {
        stage('Clone repository') { 
            steps { 
                script{
                checkout scm
                }
            }
        }
        stage('Build') {
            steps {
                script {
                    dockerImageWeb = docker.build("web:${env.BUILD_NUMBER}", "./web")
                    dockerImageCart = docker.build("cart:${env.BUILD_NUMBER}", "./cart")
                    dockerImageCatalogue = docker.build("catalogue:${env.BUILD_NUMBER}", "./catalogue")
                    dockerImageDispatch = docker.build("dispatch:${env.BUILD_NUMBER}", "./dispatch")
                    dockerImageMongo = docker.build("mongo:${env.BUILD_NUMBER}", "./mongo")
                    dockerImageMysql = docker.build("mysql:${env.BUILD_NUMBER}", "./mysql")
                    dockerImagePayment = docker.build("payment:${env.BUILD_NUMBER}", "./payment")
                    dockerImageRatings = docker.build("ratings:${env.BUILD_NUMBER}", "./ratings")
                    dockerImageShipping = docker.build("shipping:${env.BUILD_NUMBER}", "./shipping")
                    dockerImageUser = docker.build("user:${env.BUILD_NUMBER}", "./user")
                }
            } 
        }
        stage('Push') {
            steps {
                script{
                docker.withRegistry('https://339712782795.dkr.ecr.us-east-2.amazonaws.com/web', 'ecr:us-east-2:aws-credentials') {
                    dockerImageWeb.push("${env.BUILD_NUMBER}")
                    dockerImageWeb.push("latest")
                }
                    docker.withRegistry('https://339712782795.dkr.ecr.us-east-2.amazonaws.com/cart', 'ecr:us-east-2:aws-credentials') {
                    dockerImageCart.push("${env.BUILD_NUMBER}")
                    dockerImageCart.push("latest")
                }
                docker.withRegistry('https://339712782795.dkr.ecr.us-east-2.amazonaws.com/catalogue', 'ecr:us-east-2:aws-credentials') {
                    dockerImageCatalogue.push("${env.BUILD_NUMBER}")
                    dockerImageCatalogue.push("latest")
                }

                docker.withRegistry('https://339712782795.dkr.ecr.us-east-2.amazonaws.com/dispatch', 'ecr:us-east-2:aws-credentials') {
                    dockerImageDispatch.push("${env.BUILD_NUMBER}")
                    dockerImageDispatch.push("latest")
                }

                docker.withRegistry('https://339712782795.dkr.ecr.us-east-2.amazonaws.com/mongo', 'ecr:us-east-2:aws-credentials') {
                    dockerImageMongo.push("${env.BUILD_NUMBER}")
                    dockerImageMongo.push("latest")
                }

                docker.withRegistry('https://339712782795.dkr.ecr.us-east-2.amazonaws.com/mysql', 'ecr:us-east-2:aws-credentials') {
                    dockerImageMysql.push("${env.BUILD_NUMBER}")
                    dockerImageMysql.push("latest")
                }

                docker.withRegistry('https://339712782795.dkr.ecr.us-east-2.amazonaws.com/payment', 'ecr:us-east-2:aws-credentials') {
                    dockerImagePayment.push("${env.BUILD_NUMBER}")
                    dockerImagePayment.push("latest")
                }

                docker.withRegistry('https://339712782795.dkr.ecr.us-east-2.amazonaws.com/ratings', 'ecr:us-east-2:aws-credentials') {
                    dockerImageRatings.push("${env.BUILD_NUMBER}")
                    dockerImageRatings.push("latest")
                }

                docker.withRegistry('https://339712782795.dkr.ecr.us-east-2.amazonaws.com/shipping', 'ecr:us-east-2:aws-credentials') {
                    dockerImageShipping.push("${env.BUILD_NUMBER}")
                    dockerImageShipping.push("latest")
                }

                docker.withRegistry('https://339712782795.dkr.ecr.us-east-2.amazonaws.com/user', 'ecr:us-east-2:aws-credentials') {
                    dockerImageUser.push("${env.BUILD_NUMBER}")
                    dockerImageUser.push("latest")
                }

            }
            }
        }
        stage('Deploy') {
            steps{
                withCredentials([[
                $class: 'AmazonWebServicesCredentialsBinding',
                accessKeyVariable: 'AWS_ACCESS_KEY_ID',
                secretKeyVariable: 'AWS_SECRET_ACCESS_KEY',
                credentialsId: 'aws-credentials']]) 
                {
                script{
                    sh 'aws eks --region us-east-2 update-kubeconfig --name project1-eks-cluster-1'
                    sh 'helm install --set image.repo=339712782795.dkr.ecr.us-east-2.amazonaws.com --set image.version=latest project1-release ./project1-helm'
                }
                }
            }
        }
    }
}
