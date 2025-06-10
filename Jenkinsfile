pipeline {
    agent any

    stages {
        stage('Install kubectl') {
            steps {
                sh '''
                    curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
                    chmod +x kubectl
                    sudo mv kubectl /usr/local/bin/
                    kubectl version --client
                '''
            }
}

        stage('Deploy to Kubernetes') {
            steps {
                script {
                    kubeconfig(caCertificate: 'LS0tLS1CRUdJTiBDRVJUSUZJQ0FURS0tLS0tCk1JSURCakNDQWU2Z0F3SUJBZ0lCQVRBTkJna3Foa2lHOXcwQkFRc0ZBREFWTVJNd0VRWURWUVFERXdwdGFXNXAKYTNWaVpVTkJNQjRYRFRJMU1EWXdOakV4TXpnek9Gb1hEVE0xTURZd05URXhNemd6T0Zvd0ZURVRNQkVHQTFVRQpBeE1LYldsdWFXdDFZbVZEUVRDQ0FTSXdEUVlKS29aSWh2Y05BUUVCQlFBRGdnRVBBRENDQVFvQ2dnRUJBTElIClNBcCswaU9JdkNKMDluSk5zQ0dzakpjeWV4UjFXc1p3cVJKR0Q3Tml1MVZ6VVVsYnFXUGhuMHZ2d3RkejRjaHMKMmlpNGJjNUJmOXQ2RUpDWjA4cis2NyttS0FFTXFQcmhsZnFZd3NFZy9WZzNjLzg2SVczQ0VvdVp0UTczb2dMRgpxL2UrRzNJNlFIbzZHaGNmeWdxQzR0ZEtndkdOSFNTVnlCSlNiK2VyM3J4QjRvLzMvZ3N3UmtuY2tUVUtjTGIyCmNxQUVxLzJwZ1kveGo3TTBGUDBHWTJSWGVMcDdYdGdQekxmVGFrNUV1cmpMaU5ja0dGWmk1NVhsY3J6MmFsWTMKSDJ4c0g0Mm1QOWExMTBqbFNnUkFYRHBadzk3YnVaS3ZUOVlCdWIySENJallTWVhzcEpMajlnZytLbE5hZGRYZAp6Z2RNbmNCTjByV0lmMGlKWHdFQ0F3RUFBYU5oTUY4d0RnWURWUjBQQVFIL0JBUURBZ0trTUIwR0ExVWRKUVFXCk1CUUdDQ3NHQVFVRkJ3TUNCZ2dyQmdFRkJRY0RBVEFQQmdOVkhSTUJBZjhFQlRBREFRSC9NQjBHQTFVZERnUVcKQkJSNWFwRGJqQnFkZ1MweHlnWFllVmZ6NElpZEpEQU5CZ2txaGtpRzl3MEJBUXNGQUFPQ0FRRUFkcmxxZ1V5ZAp1bTIzaThIUDBvTnlucDQ0RVMzRzJlNnNLaDhwY0pGVlN0UVBuLzhuUDFkcE5SdU9DWHZxNmhnSU5sQWl1UHVTCjhPWU5DbVdUWTNOZXFwT0lTdE42dWIwVDR5dnpSdjlPVzZnaHhPemtGeWQ5MUdOOHhpWXh5WTl5T2FUUDdDNGoKWG9xTitBOXZ2Smt0cUlaNmViWXFWUFJ3dkJXT2NwSExvUlVQcytSQVBieGxKbjZVSGhxL0kvSUZqOW1zb21uMwoyUnpWbTVFb0ZxOHVnV3hPV3FSY1N4dExPV3FKa2poekpnTWtiOE03aThaWkw4ZDhrRys4QWlVVjZEUVRtYnBtClR6SE1JR2N3VkNkUHFLQm9nS0R1d3ZCQmJFTWN2dWNJem8wUmxMYUg0aUxLeDZXT1RzM2p3ZTlPOUxDVHFhb0sKd1hUY3kzS2ZCV3ZNV1E9PQotLS0tLUVORCBDRVJUSUZJQ0FURS0tLS0tCg==', 
                    credentialsId: 'kubeconfig', 
                    serverUrl: 'https://127.0.0.1:61524') {
                        sh 'kubectl apply -f webapp.yaml'
}
                }
            }
        }
    }
}