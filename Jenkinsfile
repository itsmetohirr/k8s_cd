pipeline {
    agent {
        docker {
            image 'bitnami/kubectl:1.33.1'
            args "-v /root/.kube:/root/.kube --entrypoint=''"
        }
    }

    stages{
        stage('check') {
            steps {
                sh 'kubectl'
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                withCredentials([file(credentialsId: 'kubeconfig', variable: 'KUBECONFIG')]) {
                    sh 'kubectl cluster-info'
                }
            }
        }
    }
}
