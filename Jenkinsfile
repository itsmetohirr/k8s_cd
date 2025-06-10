pipeline {
    agent {
        docker {
            image 'bitnami/kubectl:latest'
            args '-v $HOME/.kube:/root/.kube' // mounting kubeconfig
        }
    } 

    environment {
        KUBECONFIG = '/root/.kube/config' // container path
    }

    stages {
        stage('Deploy to Kubernetes') {
            steps {
                script {
                    sh 'kubectl apply -f webapp.yaml'
                }
            }
        }
    }
}
