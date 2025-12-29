pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') { 
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'rameks-cluster', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://17376E29450EF7411F2168D3DCF2EEFB.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    sleep 60
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'rameks-cluster', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://17376E29450EF7411F2168D3DCF2EEFB.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl get all -n webapps"
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
