pipeline {
    agent any

    stages {
        stage('deploy to kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-2', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://56B6473C45632EDE060271137531DACB.gr7.us-east-1.eks.amazonaws.com']]) {
                sh "kubectl apply -f deployment-service.yml"
                sleep 60 
}
            }
        }
         stage('verify deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-2', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://56B6473C45632EDE060271137531DACB.gr7.us-east-1.eks.amazonaws.com']]) {
                sh "kubectl get all -n webapps"
}
            }
        }
    }
}
