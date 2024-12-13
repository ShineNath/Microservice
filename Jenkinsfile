pipeline {
    agent any

    environment {
        K8S_NAMESPACE = "webapps"
        K8S_SERVER_URL = "https://dev-env-dns-3ompk1cb.hcp.centralindia.azmk8s.io"
    }

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'DEV-ENV', contextName: '', credentialsId: 'k8-token', namespace: K8S_NAMESPACE, serverUrl: K8S_SERVER_URL]]) {
                    sh "kubectl apply -f deployment-service.yml --validate=false"
                }
            }
        }
        
        stage('Verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'DEV-ENV', contextName: '', credentialsId: 'k8-token', namespace: K8S_NAMESPACE, serverUrl: K8S_SERVER_URL]]) {
                    sh "kubectl get svc -n ${K8S_NAMESPACE}"
                }
            }
        }
    }
}
