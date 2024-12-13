pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
              withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'https://portal.azure.com/#@alameentrustedhandsfintech.onmicrosoft.com/resource/subscriptions/a3a354a6-a3df-4102-8e68-9dd0169a969b/resourceGroups/FullStackApp-Dev/providers/Microsoft.ContainerService/managedClusters/DEV-ENV/overview:~:text=FullStackApp%2DDev-,DEV%2DENV,-Kubernetes%20service', contextName: '', credentialsId: '', namespace: '', serverUrl: 'dev-env-dns-3ompk1cb.hcp.centralindia.azmk8s.io']]) {
                   sh "kubectl apply -f deployment-service.yml"
                }
            }
        }
        
        stage('verify Deployment') {
             steps {
                 withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'https://portal.azure.com/#@alameentrustedhandsfintech.onmicrosoft.com/resource/subscriptions/a3a354a6-a3df-4102-8e68-9dd0169a969b/resourceGroups/FullStackApp-Dev/providers/Microsoft.ContainerService/managedClusters/DEV-ENV/overview:~:text=FullStackApp%2DDev-,DEV%2DENV,-Kubernetes%20service', contextName: '', credentialsId: '', namespace: '', serverUrl: 'dev-env-dns-3ompk1cb.hcp.centralindia.azmk8s.io']]) {
                    sh "kubectl get svc -n default"
                }
            
            }
        }
    }
}

