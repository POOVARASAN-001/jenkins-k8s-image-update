
pipeline {
    agent any

    environment {
        KUBECTL = 'D:\\DockerApp\\resources\\bin\\kubectl.exe'
        KUBECONFIG = 'C:\\Users\\POOVARASAN\\.kube\\config'
    }

    stages {
        stage('Create Deployment') {
            steps {
                bat '"%KUBECTL%" apply -f deployment.yaml'
            }
        }

        stage('Update Docker Image') {
            steps {
                bat '"%KUBECTL%" set image deployment/image-update-app nginx=nginx:stable'
            }
        }

        stage('Verify Update') {
            steps {
                bat '"%KUBECTL%" rollout status deployment/image-update-app --timeout=180s'
                bat '"%KUBECTL%" get deployment image-update-app -o wide'
            }
        }
    }
}
