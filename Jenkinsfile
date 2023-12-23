pipeline {
    agent any
    
    environment{
        
        SCANNER_HOME = tool 'sonar-scanner'
    }

    stages {
        
        stage('Git Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/kaustika940/10-Tier-MicroService-Application.git'
            }
        }
        
        stage('SonarQube Analysis') {
            steps {
                
                withSonarQubeEnv('sonar') {
                    sh ''' $SCANNER_HOME/bin/sonar-scanner -Dsonar.projectKey=10-Tier -Dsonar.projectName=10-Tier -Dsonar.java.binaries=. '''
   
                     }
                 }
            
        }
        
        stage('adservice') {
            steps {
                script{
                    withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                        dir('/var/lib/jenkins/workspace/10-Tier-Microservice/src/adservice/') {
                            sh 'docker build -t kaustika1997/adservice:latest .'
                            sh 'docker push kaustika1997/adservice:latest'
                            sh 'docker rmi kaustika1997/adservice:latest'
    
                        }  
                    }
                }
            }
        }
        
        stage('cartservice') {
            steps {
                script{
                    withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                        dir('/var/lib/jenkins/workspace/10-Tier-Microservice/src/cartservice/src/') {
                            sh 'docker build -t kaustika1997/cartservice:latest .'
                            sh 'docker push kaustika1997/cartservice:latest'
                            sh 'docker rmi kaustika1997/cartservice:latest'
    
                        }  
                    }
                }
            }
        }
        
        stage('checkoutservice') {
            steps {
                script{
                    withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                        dir('/var/lib/jenkins/workspace/10-Tier-Microservice/src/checkoutservice/') {
                            sh 'docker build -t kaustika1997/checkoutservice:latest .'
                            sh 'docker push kaustika1997/checkoutservice:latest'
                            sh 'docker rmi kaustika1997/checkoutservice:latest'
    
                        }  
                    }
                }
            }
        }
        
        stage('currencyservice') {
            steps {
                script{
                    withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                        dir('/var/lib/jenkins/workspace/10-Tier-Microservice/src/currencyservice/') {
                            sh 'docker build -t kaustika1997/currencyservice:latest .'
                            sh 'docker push kaustika1997/currencyservice:latest'
                            sh 'docker rmi kaustika1997/currencyservice:latest'
    
                        }  
                    }
                }
            }
        }
        
        stage('emailservice') {
            steps {
                script{
                    withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                        dir('/var/lib/jenkins/workspace/10-Tier-Microservice/src/emailservice/') {
                            sh 'docker build -t kaustika1997/emailservice:latest .'
                            sh 'docker push kaustika1997/emailservice:latest'
                            sh 'docker rmi kaustika1997/emailservice:latest'
    
                        }  
                    }
                }
            }
        }
        
        stage('frontend') {
            steps {
                script{
                    withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                        dir('/var/lib/jenkins/workspace/10-Tier-Microservice/src/frontend/') {
                            sh 'docker build -t kaustika1997/frontend:latest .'
                            sh 'docker push kaustika1997/frontend:latest'
                            sh 'docker rmi kaustika1997/frontend:latest'
    
                        }  
                    }
                }
            }
        }
        stage('loadgenerator') {
            steps {
                script{
                    withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                        dir('/var/lib/jenkins/workspace/10-Tier-Microservice/src/loadgenerator/') {
                            sh 'docker build -t kaustika1997/loadgenerator:latest .'
                            sh 'docker push kaustika1997/loadgenerator:latest'
                            sh 'docker rmi kaustika1997/loadgenerator:latest'
    
                        }  
                    }
                }
            }
        }
        
        stage('paymentservice') {
            steps {
                script{
                    withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                        dir('/var/lib/jenkins/workspace/10-Tier-Microservice/src/paymentservice/') {
                            sh 'docker build -t kaustika1997/paymentservice:latest .'
                            sh 'docker push kaustika1997/paymentservice:latest'
                            sh 'docker rmi kaustika1997/paymentservice:latest'
    
                        }  
                    }
                }
            }
        }
        
        stage('productcatalogservice') {
            steps {
                script{
                    withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                        dir('/var/lib/jenkins/workspace/10-Tier-Microservice/src/productcatalogservice/') {
                            sh 'docker build -t kaustika1997/productcatalogservice:latest .'
                            sh 'docker push kaustika1997/productcatalogservice:latest'
                            sh 'docker rmi kaustika1997/productcatalogservice:latest'
    
                        }  
                    }
                }
            }
        }
        
        stage('recommendationservice') {
            steps {
                script{
                    withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                        dir('/var/lib/jenkins/workspace/10-Tier-Microservice/src/recommendationservice/') {
                            sh 'docker build -t kaustika1997/recommendationservice:latest .'
                            sh 'docker push kaustika1997/recommendationservice:latest'
                            sh 'docker rmi kaustika1997/recommendationservice:latest'
    
                        }  
                    }
                }
            }
        }
        
        stage('shippingservice') {
            steps {
                script{
                    withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                        dir('/var/lib/jenkins/workspace/10-Tier-Microservice/src/shippingservice/') {
                            sh 'docker build -t kaustika1997/shippingservice:latest .'
                            sh 'docker push kaustika1997/shippingservice:latest'
                            sh 'docker rmi kaustika1997/shippingservice:latest'
    
                        }  
                    }
                }
            }
        }
        
        stage('K8-Deploy') {
            steps {
                withKubeConfig(caCertificate: '', clusterName: 'my-eks2', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', restrictKubeConfigAccess: false, serverUrl: 'https://03164DDFFC11D3D31CFE4932C3BAE4A0.sk1.us-east-1.eks.amazonaws.com') {
                    sh 'kubectl apply -f deployment-service.yml'
                    sh 'kubectl get pods'
                    sh 'kubectl get svc'
   
                }
            }
        }
       
    }
}

