pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/ShahidKhan48/application-projects.git'
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                withKubeConfig([credentialsId: 'k8s-cred']) {
                    sh '''
                    kubectl apply -f nginx-deployment.yaml -n jenkins
                    kubectl apply -f nginx-service.yaml -n jenkins
                    '''
                }
            }
        }
    }
}
