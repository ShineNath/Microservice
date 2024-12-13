pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                // Use the correct Kubernetes credentials stored in Jenkins
                withKubeCredentials(credentialsId:k8-token) {
                    sh "kubectl apply -f deployment-service.yml --validate=false"
                }
            }
        }
        
        stage('Verify Deployment') {
            steps {
                // Use the correct Kubernetes credentials again for verification
                withKubeCredentials(credentialsId:k8-token) {
                    sh "kubectl get svc -n default"
                }
            }
        }
    }
}


