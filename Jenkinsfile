pipeline {
    agent any

    tools {
        terraform 'Terraform'
    }

    stages {
        stage("Init") {
            steps {
                withCredentials([
                    usernamePassword(credentialsId: 'aws-creds', 
                                     usernameVariable: 'AWS_ACCESS_KEY_ID', 
                                     passwordVariable: 'AWS_SECRET_ACCESS_KEY')
                ]) {
                    sh 'terraform init'
                }
            }
        }

        stage("Plan") {
            steps {
                withCredentials([
                    usernamePassword(credentialsId: 'aws-creds', 
                                     usernameVariable: 'AWS_ACCESS_KEY_ID', 
                                     passwordVariable: 'AWS_SECRET_ACCESS_KEY')
                ]) {
                    sh 'terraform plan'
                }
            }
        }

        stage("Apply") {
            steps {
                withCredentials([
                    usernamePassword(credentialsId: 'aws-creds', 
                                     usernameVariable: 'AWS_ACCESS_KEY_ID', 
                                     passwordVariable: 'AWS_SECRET_ACCESS_KEY')
                ]) {
                    sh 'terraform apply -auto-approve'
                }
            }
        }
    }
}
