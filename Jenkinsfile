pipeline {
  agent any

  stages {
    stage('Checkout') {
      steps {
        sh 'rm -rf terraform-aws-infra ansible-configs || true'
        sh 'git clone https://github.com/Pujitha-Reddy/terraform-aws-infra.git'
        sh 'git clone https://github.com/Pujitha-Reddy/ansible-configs.git'
      }
    }

    stage('Terraform Apply (LocalStack)') {
      steps {
        dir('terraform-aws-infra') {
          sh 'chmod +x run.sh'
          sh './run.sh'
          sh 'terraform output'
        }
      }
    }

    stage('Ansible Configure (Local Target)') {
      steps {
        dir('ansible-configs') {
          sh 'chmod +x run.sh'
          sh './run.sh'
        }
      }
    }

    stage('Build Demo Artifact') {
      steps {
        sh 'echo "Build complete" > build.txt'
        archiveArtifacts artifacts: 'build.txt', fingerprint: true
      }
    }
  }
}
