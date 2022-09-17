pipeline {
    agent any

    tools {
        maven 'Maven3'
    }

    stages {
        stage('Checkout') {
            steps {
                checkout([$class: 'GitSCM', 
                branches: [[name: '*/master']], 
                extensions: [], 
                userRemoteConfigs: 
                [[credentialsId: '6109ad18-92d3-428f-9457-9c29855f2ae5', 
                url: 'https://github.com/kuga01/EFK-Kubernetes']]])
            }
        }
        
        stage('K8S Deploy') {
            steps{   
                script {
                    withKubeConfig(caCertificate: '', clusterName: '', contextName: '', credentialsId: 'K8S', namespace: '', serverUrl: '') {
                    sh ('kubectl create -f counter.yaml')
                    }
                }
            }
        }   
    }
}
