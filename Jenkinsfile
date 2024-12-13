pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
               withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'DEV-ENV', contextName: '', credentialsId: '', namespace: 'webapps', serverUrl: 'dev-env-dns-acy6inej.hcp.centralindia.azmk8s.io']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    sleep 60
                   
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
               withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'DEV-ENV', contextName: '', credentialsId: '', namespace: 'webapps', serverUrl: 'dev-env-dns-acy6inej.hcp.centralindia.azmk8s.io']]) {
                    sh "kubectl get all -n webapps"
                }
            }
        }
    }
}
