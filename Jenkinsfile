pipeline  {
    agent any

    stages {
        stage('Deploy to K8s') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://72937AADAD4ECE1162EE89A4014B36D6.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    sleep 60
                }
            }
        }
         stage('Verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://72937AADAD4ECE1162EE89A4014B36D6.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl get all -n webapps"
                    
                }
            }
        }
    }
}
