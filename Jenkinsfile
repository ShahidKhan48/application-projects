pipeline {
    agent any

    stages {
        
        stage('Deploy to Kubernetes') {
            steps {
               withCredentials([file(credentialsId: 'k8s-cred', variable: 'KUBECONFIG')]) { 
                   sh ''' # Install kubectl at runtime 
                   curl -LO "https://dl.k8s.io/release/$(curl -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl" 
                   chmod +x kubectl 
                   sudo mv kubectl /usr/local/bin/ # Verify installation 
                   kubectl version --client
                   kubectl get no
                   kubectl apply -f nginx-deployment.yaml -n jenkins
                   kubectl apply -f nginx-service.yaml -n jenkins
                    '''
                }
            }
        }
    }
}
