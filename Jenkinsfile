pipeline {
    agent any

    stages {
        stage('Deploy to kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-cluster', contextName: '', credentialsId: 'kube-cred', namespace: 'webapps', serverUrl: 'https://4AF1EAFEE0E516F849E8FD4FC7625E99.sk1.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
               }
            }
        }
        stage('verify the pods') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-cluster', contextName: '', credentialsId: 'kube-cred', namespace: 'webapps', serverUrl: 'https://4AF1EAFEE0E516F849E8FD4FC7625E99.sk1.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
               }
            }
        }
    }
}
