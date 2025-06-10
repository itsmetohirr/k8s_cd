pipeline {
    agent {
        docker {
            image 'bitnami/kubectl:1.33.1'
            args "-v /root/.kube:/root/.kube --entrypoint=''"
        }
    }

    stages{
        stage('Deploy to Kubernetes') {
            steps {
                withCredentials([file(credentialsId: 'kubeconfig', variable: 'KUBECONFIG')]) {
                    sh '''
                    echo "🔍 Verifying cluster access..."
                    kubectl get pods

                    echo "🚀 Applying deployment..."
                    kubectl apply -f k8s/deployment.yaml

                    echo "🌐 Applying service..."
                    kubectl apply -f k8s/service.yaml
                    '''
                }
            }
    }
}
