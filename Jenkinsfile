pipeline {
    agent any
    environment {
        SCANNER_HOME = tool 'sonar-scanner'

   }

    stages {
            stage('SonarQube') {
             steps {
                withSonarQubeEnv('sonar-scanner') {
                    sh '''$SCANNER_HOME/bin/sonar-scanner -Dsonar.projectKey=Microservice_Deployment -Dsonar.ProjectName=Microservice_Deployment -Dsonar.java.binaries=.'''
                }
            }
        }
            stage('adservice') {
              steps {
               script {
                 withDockerRegistry(credentialsId: 'dockerpass', toolName: 'docker') {
                    dir('/var/lib/jenkins/workspace/Microservice_Deployment/src/adservice/') {
                        sh "docker build -t ashow4all/adservice:latest ."
                        sh "docker push ashow4all/adservice:latest"
                        sh "docker rmi ashow4all/adservice:latest"
                        sh 'docker system prune -a -f --volumes'
                    }
                }
            }
        }
            }
            stage('cartservice') {
              steps {
               script {
                 withDockerRegistry(credentialsId: 'dockerpass', toolName: 'docker') {
                    dir("/var/lib/jenkins/workspace/Microservice_Deployment/src/cartservice/src/") {
                        sh "docker build -t ashow4all/cartservice:latest ."
                        sh "docker push ashow4all/cartservice:latest"
                        sh "docker rmi ashow4all/cartservice:latest"
                        sh 'docker system prune -a -f --volumes'
                    }
                }
            }
        }
       }
            stage('checkoutservice') {
              steps {
               script {
                 withDockerRegistry(credentialsId: 'dockerpass', toolName: 'docker') {
                    dir("/var/lib/jenkins/workspace/Microservice_Deployment/src/checkoutservice/") {
                        sh "docker build -t ashow4all/checkoutservice:latest ."
                        sh "docker push ashow4all/checkoutservice:latest"
                        sh "docker rmi ashow4all/checkoutservice:latest"
                        sh 'docker system prune -a -f --volumes'
                    }
                }
            }
        }
            }
            stage('currencyservice') {
              steps {
               script {
                 withDockerRegistry(credentialsId: 'dockerpass', toolName: 'docker') {
                    dir("/var/lib/jenkins/workspace/Microservice_Deployment/src/currencyservice/") {
                        sh "docker build -t ashow4all/currencyservice:latest ."
                        sh "docker push ashow4all/currencyservice:latest"
                        sh "docker rmi ashow4all/currencyservice:latest"
                        sh 'docker system prune -a -f --volumes'
                    }
                }
            }
        }

            }
            stage('emailservice') {
              steps {
               script {
                 withDockerRegistry(credentialsId: 'dockerpass', toolName: 'docker') {
                    dir("/var/lib/jenkins/workspace/Microservice_Deployment/src/emailservice/") {
                        sh "docker build -t ashow4all/emailservice:latest ."
                        sh "docker push ashow4all/emailservice:latest"
                        sh "docker rmi ashow4all/emailservice:latest"
                        sh 'docker system prune -a -f --volumes'
                    }
                }
            }
        }
            }
            stage('frontend') {
              steps {
               script {
                 withDockerRegistry(credentialsId: 'dockerpass', toolName: 'docker') {
                    dir("/var/lib/jenkins/workspace/Microservice_Deployment/src/frontend/") {
                        sh "docker build -t ashow4all/frontend:latest ."
                        sh "docker push ashow4all/frontend:latest"
                        sh "docker rmi ashow4all/frontend:latest"
                        sh 'docker system prune -a -f --volumes'
                    }
                }
            }
        }
            }
            stage('loadgenerator') {
              steps {
               script {
                 withDockerRegistry(credentialsId: 'dockerpass', toolName: 'docker') {
                    dir("/var/lib/jenkins/workspace/Microservice_Deployment/src/loadgenerator/") {
                        sh "docker build -t ashow4all/loadgenerator:latest ."
                        sh "docker push ashow4all/loadgenerator:latest"
                        sh "docker rmi ashow4all/loadgenerator:latest"
                        sh 'docker system prune -a -f --volumes'
                    }
                }
            }
        }
            }
             stage('paymentservice') {
              steps {
               script {
                 withDockerRegistry(credentialsId: 'dockerpass', toolName: 'docker') {
                    dir("/var/lib/jenkins/workspace/Microservice_Deployment/src/paymentservice/") {
                        sh "docker build -t ashow4all/paymentservice:latest ."
                        sh "docker push ashow4all/paymentservice:latest"
                        sh "docker rmi ashow4all/paymentservice:latest"
                        sh 'docker system prune -a -f --volumes'
                    }
                }
            }
        }
             }
             stage('productcatalogservice') {
              steps {
               script {
                 withDockerRegistry(credentialsId: 'dockerpass', toolName: 'docker') {
                    dir("/var/lib/jenkins/workspace/Microservice_Deployment/src/productcatalogservice/") {
                        sh "docker build -t ashow4all/productcatalogservice:latest ."
                        sh "docker push ashow4all/productcatalogservice:latest"
                        sh "docker rmi ashow4all/productcatalogservice:latest"
                        sh 'docker system prune -a -f --volumes'
                    }
                }
            }
        }
             }
             stage('recommendationservice') {
              steps {
               script {
                 withDockerRegistry(credentialsId: 'dockerpass', toolName: 'docker') {
                    dir("/var/lib/jenkins/workspace/Microservice_Deployment/src/recommendationservice/") {
                        sh "docker build -t ashow4all/recommendationservice:latest ."
                        sh "docker push ashow4all/recommendationservice:latest"
                        sh "docker rmi ashow4all/recommendationservice:latest"
                        sh 'docker system prune -a -f --volumes'
                    }
                }
            }
        }
             }
             stage('shippingservice') {
              steps {
               script {
                 withDockerRegistry(credentialsId: 'dockerpass', toolName: 'docker') {
                    dir("/var/lib/jenkins/workspace/Microservice_Deployment/src/shippingservice/") {
                        sh "docker build -t ashow4all/shippingservice:latest ."
                        sh "docker push ashow4all/shippingservice:latest"
                        sh "docker rmi ashow4all/shippingservice:latest"
                        sh 'docker system prune -a -f --volumes'
                    }
                }
            }
        }
    }

              stage('EKS-Deployment') {
            steps {
                withKubeConfig(caCertificate: '', clusterName: 'myAppp-eks-cluster', contextName: '', credentialsId: 'k8s', namespace: 'webapps', restrictKubeConfigAccess: false, serverUrl: 'https://EFCB64260B9B6A2BB1C24D940D0745A4.yl4.us-west-2.eks.amazonaws.com') {
                    sh 'kubectl apply -f deployment-service.yaml'
                    sh 'kubectl get pods'
                    sh 'kubectl get svc'

                }
                }
            }
        }
   }
