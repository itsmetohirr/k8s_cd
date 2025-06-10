pipeline {
    agent {
        docker {
            image 'bitnami/kubectl:latest'
            args '--entrypoint="" -v $HOME/.kube:/root/.kube'
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
