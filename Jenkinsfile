pipeline { 
    agent any 
    stages { 
        stage('Deploy To Kubernetes') { 
            steps { 
                withKubeCredentials(kubectlCredentials: [[
                    caCertificate: '', 
                    clusterName: 'EKS-2', 
                    contextName: '', 
                    credentialsId: 'k8-token', 
                    namespace: 'webapps', 
                    serverUrl: 'https://16915554009613A482F08D006712647D.gr7.us-east-1.eks.amazonaws.com'
                ]]) { 
                    sh "kubectl apply -f deployment-service.yml" 
                } 
            } 
        } 
        stage('Verify Deployment') { 
            steps { 
                withKubeCredentials(kubectlCredentials: [[
                    caCertificate: '', 
                    clusterName: 'EKS-2', 
                    contextName: '', 
                    credentialsId: 'k8-token', 
                    namespace: 'webapps', 
                    serverUrl: 'https://16915554009613A482F08D006712647D.gr7.us-east-1.eks.amazonaws.com'
                ]]) { 
                    sh "kubectl get svc -n webapps" 
                } 
            } 
        } 
    } 
}
