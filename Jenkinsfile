pipeline {
    agent any

    stages {
        stage('Deploy') {
            steps {
                withKubeConfig(credentialsId: 'kubeconfig') {
                    sh 'kubectl apply -f webapp.yaml'
                }
            }
        }
    }
}
