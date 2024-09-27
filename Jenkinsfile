pipeline {
    agent any

    stages {
        stage('Deploy to Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: ' EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://DC13D891585C6858B3361C699B5B68E2.sk1.us-east-1.eks.amazonaws.com']]) {
                 sh "kubectl apply -f deployment-service.yml"
                }
            }
        }
        
        stage('Verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: ' EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://DC13D891585C6858B3361C699B5B68E2.sk1.us-east-1.eks.amazonaws.com']]) {
                 sh "kubectl get svc -n webapps"
                 }
            }
        }
    }
}
