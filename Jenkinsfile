pipeline {
    agent any

    stages {
        stage('Deploy to Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://52E5CE201B31FC16C094D932E6882ACA.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    slepp 60
                }
            }
        }
    }
    stages {
        stage('Verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://52E5CE201B31FC16C094D932E6882ACA.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl get all -n webapps"
                }
            }
        }
    }
}
