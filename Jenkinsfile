pipeline {
  agent any

  environment {
    AWS_ACCESS_KEY_ID = credentials('aws-access')      // set these in Jenkins credentials
    AWS_SECRET_ACCESS_KEY = credentials('aws-secret')
  }

  stages {
    stage('Init') {
      steps {
        dir('terraform-ec2') {
          sh 'terraform init'
        }
      }
    }

    stage('Plan') {
      steps {
        dir('terraform-ec2') {
          sh 'terraform plan'
        }
      }
    }

    stage('Apply') {
      steps {
        dir('terraform-ec2') {
          sh 'terraform apply -auto-approve'
        }
      }
    }
  }
}
