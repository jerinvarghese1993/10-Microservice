pipeline {
    agent { label 'slave01' } 
    stages {
        stage('Deploy to AKS') {
            steps {
                withKubeConfig(caCertificate: '', clusterName: 'jango-AKS', contextName: '', credentialsId: 'kube-config', namespace: '', restrictKubeConfigAccess: false, serverUrl: 'jango-aks-dns-lye6ebog.hcp.westus3.azmk8s.io') {
                    sh 'kubectl apply -f deployment-service.yml'
                }
            }
        }
    }
}
