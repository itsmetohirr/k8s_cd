pipeline {
    agent {
        docker {
            image 'bitnami/kubectl:1.33.1'
            args "-v /root/.kube:/root/.kube --entrypoint=''"
        }
    }

    stages{
        stage("check"){
            steps{
                sh 'echo Hello word'
            }
        }

        stage('Deploy to k8s'){
            steps{
                sh 'kubectl cluster-info'
            }
        }
    }
}
