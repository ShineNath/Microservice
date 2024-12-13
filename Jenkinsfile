pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
               withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'DEV-ENV', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'dev-env-dns-3ompk1cb.hcp.centralindia.azmk8s.io']]) {
                    sh "kubectl apply -f deployment-service.yml"
                }
            }
        }
        
        stage('Verify Deployment') {
            steps {
              withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'DEV-ENV', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'dev-env-dns-3ompk1cb.hcp.centralindia.azmk8s.io']]) {
                    sh "kubectl get svc -n webapps"
                    }
                }
            }
        }
    }
}


