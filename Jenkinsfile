pipeline {
    agent any

    stages {
        
        stage('Deploy to Kubernetes') {
            steps {
                withKubeConfig([credentialsId: 'k8s-cred']) {
                    sh '''
                    kubectl get no
                    kubectl apply -f nginx-deployment.yaml -n jenkins
                    kubectl apply -f nginx-service.yaml -n jenkins
                    '''
                }
            }
        }
    }
}
