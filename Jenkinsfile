pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                // Use the correct Kubernetes credentials stored in Jenkins
                withKubeCredentials(credentialsId: 'kube-id') {
                    sh "kubectl apply -f deployment-service.yml --validate=false"
                }
            }
        }
        
        stage('Verify Deployment') {
            steps {
                // Use the correct Kubernetes credentials again for verification
                withKubeCredentials(credentialsId: 'kube-id') {
                    sh "kubectl get svc -n default"
                }
            }
        }
    }
}


