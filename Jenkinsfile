pipeline {
  agent any

  stages {
    stage('Checkout') {
      steps {
        sh 'rm -rf terraform-aws-infra ansible-configs || true'

        script {
          def parts = env.GIT_URL.tokenize('/')
          def ghUser = parts[3]
          sh "git clone https://github.com/${ghUser}/terraform-aws-infra.git"
          sh "git clone https://github.com/${ghUser}/ansible-configs.git"
        }
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
