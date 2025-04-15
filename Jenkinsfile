pipeline{
    agent any
    tools {
        terraform 'Terraform'
    }
    environment {
        AWS_ACCESS_KEY_ID = credentials('aws-creds')
        AWS_SECRET_ACCESS_KEY = credentials('aws-creds')
    }

    stages{
        stage("Init"){
            steps{
                sh 'terraform init'
            }
        }
        stage("Plan"){
            steps{
                sh 'terraform plan'
            }
        }

        stage("Apply"){
            steps{
                sh 'terraform apply -auto-approve'
            }
        }
    }
}
