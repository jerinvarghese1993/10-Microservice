pipeline {
    agent { label 'slave01' }

    stages {
        stage('Deploy to K8s Cluster') {
            steps {
                withKubeConfig(caCertificate: '', clusterName: 'jango-AKS', contextName: '', credentialsId: 'kube-config', namespace: '', restrictKubeConfigAccess: false, serverUrl: 'jango-aks-dns-iei7dxgp.hcp.westus3.azmk8s.io') {
                    sh 'kubectl apply -f deployment-service.yml'
                }
            }
        }
    }
}
