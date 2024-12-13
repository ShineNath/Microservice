pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
               withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'DEV-ENV', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'dev-env-dns-acy6inej.hcp.centralindia.azmk8s.io']]) {
                    sh "kubectl apply -f depoyment-service.yml"
                    sleep 60
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
               withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'DEV-ENV', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'dev-env-dns-acy6inej.hcp.centralindia.azmk8s.io']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
