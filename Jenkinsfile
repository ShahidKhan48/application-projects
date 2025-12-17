pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main',
                url: 'https://github.com/ShahidKhan48/application-projects.git',
                credentialsId: 'github-cred'
            }
        }


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
