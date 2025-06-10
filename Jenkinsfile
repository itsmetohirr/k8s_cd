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
                sh 'ls ~/.kube'
            }
        }
    }
}
