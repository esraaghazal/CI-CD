pipeline {

  environment {
    dockerimagename = "esraaghazal/nodeapp"
    dockerImage = ""
  }

  agent any

  stages {

    stage('Checkout Source') {
      steps {
        git 'https://github.com/esraaghazal/CI-CD.git'
      }
    }

    stage('Build Image') {
      steps {
        script {
          dockerImage = docker.build(dockerimagename)
        }
      }
    }

    stage('Push Image') {
      environment {
        registryCredential = 'dockerhublogin'
      }
      steps {
        script {
          docker.withRegistry('https://registry.hub.docker.com', registryCredential) {
            dockerImage.push("latest")
          }
        }
      }
    }

    stage('Deploy to Kubernetes') {
      steps {
        withCredentials([file(credentialsId: 'kubernetes', variable: 'KUBECONFIG')]) {
          sh 'kubectl apply -f deployment.yml'
          sh 'kubectl apply -f service.yml'
        }
      }
    }

  }
}
