pipeline {
    agent { label 'slave01' }
  
    environment {
        registryName = 'jangoregistry'
        registryUrl = 'jangoregistry.azurecr.io'
        registryCredentialId = 'c11253f0-6a37-453d-ad1a-8481993d8f3d'
        imageName = 'productcatalogservice'
    }

    stages {
         stage('Build the image using docker') {
            steps {
                script {
                    dockerImage = docker.build("${registryUrl}/${imageName}", "-f Dockerfile .")
                }
             }
        }
        stage('Upload to ACR') {
            steps {
                script {
                    docker.withRegistry("https://${registryUrl}", registryCredentialId) {
                    dockerImage.push("latest")
                    }
                }
            }
        }
    }
}
